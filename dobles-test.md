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