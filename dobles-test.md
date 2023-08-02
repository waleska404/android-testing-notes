# 3. DOBLES DE TEST


## ¿Qué son los dobles de test?:

- Se utilizan para simular el comportamiento de una dependencia de una aplicación en un entorno de pruebas, sin depender de la implementación real.
	- Permite realizar pruebas aisladas de una parte específica de la aplicación.
	- Abstracción de dependencias externas.
	- Controlar el comportamiento de esas dependencias.
- Hablaremos de 5 tipos de dobles de test:
	- Dummy
	- Stub
	- Fake
	- Spy
	- Mock


## Dummy:

- Es el más sencillo de todos: lo que hace es proporcionar una implementación vacía.
- Cumple con la firma de un método o interfaz.
- Nunca se va a llamar, porque realmente no tenemos intención de utilizar el objeto, solo queremos que cumpla con la firma para que el código compile.
- Por ejemplo en el siguiente código queremos testear la función `finishOrder()` pero necesitamos pasarle una `creditCard` al objeto `Customer` para poder crearlo, pero en la función que queremos testear, no se utiliza la `creditCard`, por tanto creamos un dummy para esta clase.

	```
	interface CreditCard {
		fun charge(amount: Double)
	}

	class CreditCardDummy : CreditCard {
		override fun charge(amount: Double) {
			// no hacemos nada
		}
	}

	class Costumer(val creditCard: CreditCard) {
		fun makePayment() {

		}

		fun finishOrder() {
			// en esta función no se utiliza la variable creditCard
		}
	}

	fun main() {
		val customer = Customer(CreditCardDummy())
		customer.finishOrder()
	}

	```


## Stub:

- Se utilizan para simular el comportamiento de una dependencia en un entorno de pruebas.
- Proporcionan respuestas predefinidas para ciertas entradas, son muy útiles para probar como se comporta la aplicación en diferentes esecenarios.
- Devuelven el mismo valor independientemente del contexto.
- Puede tener una pequeña lógica en función del valor de entrada.
- Se diferencia del `dummy` en que en este caso, si que vamos a utilizar el valor de returno del doble de test `stub`.
	```
	interface DiscountService {
		fun getDiscount(costumer: Costumer): Double
	}

	class DiscountServiceStub : DiscountService {
		override fun getDiscount(customer: Customer): Double = 0.1
	}

	class Customer {
		fun getDiscount(discountService: DiscountService): Double = discountService.getDiscount(this) // this = costumer
	}

	fun main() {
		val customer = Costumer()
		val discountService = DiscountServiceStub()
		customer.getDiscount(discountService)
	}
	```	


## Fake:

- Imitan el comportamiento real.
- Implementación simplificada.
- Útiles cuando la dependencia es compleja o cuesta mucho trabajo configurarla para un entorno de pruebas.
- El típico ejemplo de un `fake` es la base de datos, persistirla en memoria como por ejemplo en un array en vez de en disco.
- La principal diferencia con los anteriores es que se asemejan más a la realidad y suelen ser más reutilizables.

	```
	class Email

	interface EmailService {
		fun sendEmail(email: Email)
		fun getSentEmails(): List<Email>
	}

	class EmailServiceFake: EmailService {

		private val sentEmails = mutableListOf<Email>()

		override fun sendEmail(email: Email) {
			sentEmails.add(email)
		}

		override fun getSentEmails(): List<Email> = sentEmails
	}

	class Customer {
		fun sendEmail(emailService: EmailService, email: Email) {
			emailService.sendEmail(email)
		}
	}

	fun main() {
		val customer = Customer()
		val emailService = EmailServiceFake()
		customer.getDiscount(discountService)
	}
	```









