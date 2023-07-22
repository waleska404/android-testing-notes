# 2. INTRODUCCIÓN AL TESTING


## ¿Qué son los tests?:

- Ayudan a comprobar que nuestro código hace lo que tiene que hacer.
- Permiten desarrollar funcionalidades de manera completa, sin tener que probar manualmente cada camino.
- Nos obligan a crear código de calidad:
	- Cumplir principios SOLID.
	- Detectar code smells.
- Más seguridad si queremos refactorizar el código.



## Reglas FIRST:

- Son un conjunto de principios que se utilizan para diseñar y escribir tests de software de forma efectiva. 
- FIRST:
	- Fast
	- Isolated / Independent
	- Reliable / Repeteable
	- Self-contained / Self-validating
	- Timely / Thorough


## Tipos de tests:

- Unitarios:
	- Prueban una única entidad.
	- El resto de entidades:
		- Se mockean.
		- Se proveen implementaciones propias.
	- Son rápidos.
	- Son los más sencillos para empezar.
	- Cuando escribimos tests unitarios estamos testeando dando por hecho cómo se comunica el exterior con nuestra entidad, por tanto son necesarios pero no suficientes.
	- *Se ejecutan en local.*
	- Utilizaremos JUnit.
- De integración:
	- Comprueban cómo interactúan 2 o más entidades.
	- Inconveniente: Si fallan, no permiten detectar el punto de fallo (por eso son necesarios los tests unitarios).
	- Son menos propensos a modificaciones cuando el código cambia.
	- Muchos los incluyen como un tipo de Unit tests.
	- *Se ejecutan en local.*
	- Utilizaremos JUnit.
- De UI:
	- Comprueban la interfaz de usuario, cosas como que:
		- Al realizar una acción, se actualiza.
		- Los componentes están bien posicionados.
	- Son mucho más lentos y frágiles.
	- *Se ejecutan en dispositivo (instrumentación).*
	- Utilizaremos Espresso para las vistas clásicas, y para Compose, la propia librería de testing de Compose.


## TDD:

- Los tests se escriben antes que el código que los valida.
- Permite crear código ya testeado desde el principio:
	- Más robusto.
	- Código que tiende naturalmente a Clean y SOLID.
	- Los edge cases se detectan mejor.
- Inconvenientes:
	- Obliga a ejecutar mucho los tests: con Android no es especialmente rápido.
	- Hay que escribir tests de todo. Incluso algunos tests que puede que no nos aporten nada.
	- No es muy sencillo de implementar cuando estás empezando con el testing.







































