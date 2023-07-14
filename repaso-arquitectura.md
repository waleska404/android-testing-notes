# 1. REPASO DE LA AQUITECTURA


## Por qué es importante la arquitectura:

- La arquitectura al final es un conjunto de estructuras, y una definición de como esas estructuras interactúan entre ellas. Esto nos proporciona:
	- `Reglas para crear nuevo código`: menos decisiones que tomar a medida que generemos nuevo código, ya que esas decisiones ya están tomadas y consensuadas previamente. Desarrollo más rápido y revisión más rápida.
	- `Lenguaje para comunicarse`: más fluidez en la comunicación.

- La arquitectura también es muy importante en el testing. Nos permite:
	- Desacoplar componentes.
	- Probarlos de forma individualizada.
	- Más sencillez de los tests.


## Divisón por capas:

- Podemos dividir la aplicación en capas, donde cada capa tendrá ciertas responsabilidades, de tal forma que cada capa sea independiente de las otras, lo que nos permite testearlas de forma independiente.

- División por capas que recomienda Google:

![capas arquitectura](./images/capas_google.png)


## Capa de UI:

- Se basa principalmente la siguiente estructura:

![capa UI](./images/capa_ui.png)

---------------------------------------------------------

![capa UI details](./images/capa_ui_details.png)


## Capa de Datos:

- Se basa princpialmente en la siguiente estructura:

![capa data](./images/capa_data.png)

---------------------------------------------------------

![capa data details](./images/capa_data_detail.png)


- Funciones de la capa de datos:
	- Notificar de los cambios en la información, a través de funciones `suspend` en caso de operaciones únicas, o `flows` en caso de varios valores.
	- Todas los métodos en esta capa tienen que ser seguros para llamarlos desde el Main thread. Esto quiere decir que si es necesario cambiar de hilo para la ejecución, será la capa de datos la encargada de cambiar el hilo de ejecución.

- En la capa de datos puede haber una BD, en este caso utilizaremos `room`:

	![room](./images/room.png)

	- `Entities`: las tablas de una BD.
	- `Data Acces Objects`: como accedemos a esas tablas o entities. Lenguaje SQL. En el caso de los DAOs, peticiones en SQL representadas como una función (mapean la función con la petición SQL).
	- `Room Database`: la BD completa.

- Para acceder a datos remotos, en este caso vamos a utilizar `retrofit`: Nos permite definir una interfaz que mapee las peticiones al servidor a través de funciones.

- En el acceso a datos, siempre debe haber una única fuente de verdad. Que la información que muestre la UI venga de solo un sitio, porque sino lo que puede pasar es que haya desincronización en los datos que se muestran.









