# 5. TESTS DE INTEGRACIÓN


## Qué son los tests de integración:

- Nos permiten comprobar la validez de las interacciones entre los distintos componentes.

- Pero no hay consenso total:
	- Hay corrientes que los consideran tests unitarios (principalmente la corriente clásica). En este caso, se hace un uso extensivo de Fakes. Esta corriente considera que los "reales tests de integración" son los tests que prueban la integración de los componentes con sistemas externos.
	- También se usa el nombre de tests sociables.


## Qué testear:

- Las integraciones que veamos que nos pueden dar más problemas.

- Podemos hacer tests casi end to end:
	- Quitando la UI.
	- Quitando la conexión con servidores.


## Fakes:

- Dobles de test que representan al elemento que sustituyen realizando una implementación que podría sustituir a la real pero mucho más simplificada. Ejemplo típico: en vez de una BD -> array en memoria.

- La configuración inicial del código se hace un poco más fácil que con mocks.

- Con los fakes haremos la implementación de variantes de integración con sistemas exteriores.

- Devuelven el valor que se necesite.

- Ejemplo de fake relativamente complejo porque queremos tener reactividad:
	![fake complejo](./images/fake_complejo.png)