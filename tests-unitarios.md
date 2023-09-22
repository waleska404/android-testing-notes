# 4. TESTS UNITARIOS


## Qué son los tests unitarios:

- Nos permiten probar una única entidad de forma aislada. Sin que el código de otras entidades afecte sobre el test de la entidad en cuestión. De forma que si algo falla, sabemos seguro que es debido a la entidad que estamos testeando en particular.

- El resto de entidades:
	- Se mockean.
	- Se proveen implementaciones propias.

- Ventajas: son rápidos y sencillos.


## JUnit

- Framework que permite la ejecución de las clases de forma controlada. Cuando ejecutamos un test, ese test se ejecuta en un entorno con un principio y un fin en el que podemos hacer anclajes sobre los distintos pasos de ejecución, y JUnit nos permite realizar acciones en cada uno de esos pasos.

- Permite evaluar el comportamiento de las clases que ejecutamos de forma controlada.

- Conclusión: JUnit genera un entorno de ejecución donde las clases se pueden testear de forma aislada.

- Es necesario añadir la librería:
	![junit libreria](./images/junit_libreria.png)

- Por defecto los tests deben ir bajo la carpeta `test` que hay dentro de `src`. Se puede modificar mediante `gradle`.
	![carpeta defecto](./images/carpeta_defecto.png)


## Estructura de los tests

- Dentro de la clase tendremos un par de funciones opcionales que nos permitirán ejecutar acciones justo antes y después de cada test. Si por ejemplo dentro de una clase tenemos cuatro funciones marcadas con el `@Test`, la función marcada con `@Before` se ejecutará cuatro veces, una antes de cada test, y de la misma manera para la función marcada con `@After`:
	![after before](./images/after_before.png)


- Después añadimos los tests necesarios:
	![test estructura](./images/test_estructura.png)


## Mockito

- 























