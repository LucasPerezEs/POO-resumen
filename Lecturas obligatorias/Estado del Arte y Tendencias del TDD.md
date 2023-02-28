## El punto de vista de los requerimientos y del comportamiento

### ATDD: TDD ampliado 

***Acceptance Test Driven Development (ATDD)*** es una práctica de diseño de software que obtiene el producto a partir de las **pruebas de aceptación**. Se basa en la misma noción de Test-First de TDD, pero en vez de escribir pruebas de unidad, que escriben y usan los programadores, se escriben pruebas de aceptación de usuarios, en conjunto con ellos.

La idea es tomar cada requerimiento, en la forma de una ***user story***, construir varias pruebas de aceptación del usuario, y a partir de ellas construir las pruebas automáticas de aceptación, para luego escribir el código.

La premisa fundamental es que TDD se concibió para diseñar y probar código, pero los clientes no están interesados en el código, sino en que el sistema satisfaga sus necesidades con la mejor calidad posible.

### BDD: TDD mejorado 

En respuesta a las contras que se encontraron a TDD, Dan North empezó a hablar de ***Behavour Driven Development (BDD)***. 

La postura de North es que en vez de pensar en términos de pruebas, **deberíamos pensar en términos de especificaciones o comportamiento** De ese modo, se pueden validar más fácilmente con clientes y especialistas de negocio. Y poner el foco en el comportamiento logra un grado mayor de abstracción, al escribir las pruebas desde el punto de vista del consumidor, y no del productor. 

Las primeras herramientas que surgieron para realizar BDD, pusieron mucho énfasis en los cambios de nombres, suprimiendo todos los métodos test y cambiándolos por ***should o must***, de modo que parecieran especificaciones escritas en un lenguaje de programación. 

Pero también se asoció BDD a mejores prácticas, como la de escribir una clase de prueba por requerimiento (user story o caso de uso), incluso el superar la idea de que se trata de pruebas, hablando más bien de especificaciones.

BDD, como era de esperarse, sufrió algunas críticas. Entre ellas, se destacan:
- La que dice que BDD es sólo un cambio de nombre a TDD, cuidando un poco el lenguaje. Esto se puede ver en innumerables sitios web y blogs de programadores.
- La que dice que BDD es simplemente TDD bien hecho.

### BDD vs. ATDD

Lo importante es que, **tanto BDD como ATDD pusieron el énfasis en que no eran pruebas de pequeñas porciones de código lo que se desarrollaba, sino especificaciones de requerimientos ejecutables**. 

Y así como UTDD (Unit Test Driven Development) pretende ser una técnica de diseño detallado, **BDD se presenta como una de diseño basado en dominio**, y **ATDD una de requerimientos**. Ambas técnicas ponen el foco en que el software se construye para dar valor al negocio, y no debido a cuestiones técnicas, y en esto están muy alineadas con los métodos ágiles. 

En definitiva, **UTDD facilita el buen diseño de clases**, mientras que **ATDD y BDD facilitan construir el sistema correcto**.

De aquí en más, consideraremos como sinónimos a ATDD y BDD.


### STDD: ejemplos como pruebas y pruebas como ejemplos

Queriendo hacer confluir las pruebas de cliente de Kent Beck con BDD y ATDD, surgió una técnica habitualmente conocida como ***Story-Test Driven Development (STDD)***.

La idea subyacente es **usar ejemplos como parte de las especificaciones**, y que los mismos sirvan para probar la aplicación, haciendo que todos los roles se manejen con ejemplos idénticos. 

Estos requerimientos con ejemplos tienen ciertas ventajas, de las cuales las más importantes son:
- Sirven como herramienta de comunicación.
- Se expresan por extensión, en vez de con largas descripciones y reglas en prosa, propensas a interpretaciones diversas.
- Son más sencillos de acordar con los clientes, al ser más concretos.
- Evitan que se escriban ejemplos distintos, una y otra vez, con su potencial divergencia.
- Sirven como pruebas de aceptación.

En el enfoque de STDD, en cambio:
- El analista de negocio debe ser un facilitador de intercambio de conocimiento.
- El desarrollador es uno más de los participantes en la elaboración de los escenarios y ejemplos, que luego le sirven para desarrollar el producto y las pruebas técnicas.
- El tester es otro de los participantes en la elaboración de los escenarios y ejemplos, que luego le sirven para probar la aplicación.
- El cliente tiene un rol más activo, como autor principal de pruebas de aceptación con ejemplos, asistido por el resto de los interesados.

Limitaciones de este enfoque:
- A veces ocurre que al plantear los requerimientos como ejemplos se pierde la visión global del proyecto.
- Por otro lado, no todo requerimiento puede llevarse a ejemplos en el sentido de STDD. Por ejemplo, si una aplicación debe generar números al azarr, los ejemplos que podamos escribir nunca van a servir como pruebas de aceptación.


## El foco en el diseño orientado a objetos: NDD

### El problema del comportamiento
En el marco de TDD lo primero que hacemos es establecer la interfaz de nuestros objetos y escribir pruebas sobre ellos suponiendo que tienen esa interfaz. Por lo tanto, el encapsulamiento de los objetos se debe garantizar con ejemplos antes de pasar a la implementación. 

Los frameworks tradicionales de UTDD suelen verificar el comportamiento de los objetos, verificando el cambio de estado provocado por determinados mensajes recibidos por ellos, o los valores devueltos como consecuencia del envío de otros mensajes. Ahora bien, esta forma de verificación tiene dos problemas:

1) No siempre el comportamiento de un objeto puede evaluarse por sus cambios de estado o por los valores que devuelve. Por ejemplo, ¿qué pasa si el propósito de un mensaje es que el objeto receptor imprima algo en una impresora?
2) Para chequear el estado en que queda un objeto luego del envío de un mensaje, hay ocasiones en que necesitamos métodos de consulta que la clase del objeto no tiene,
y nos vemos obligados a cambiar la interfaz de la misma solamente para las pruebas.

### Una propuesta de solución: NDD
