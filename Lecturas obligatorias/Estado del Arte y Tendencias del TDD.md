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
Como propuesta de solución para este problema, Steve Freeman plantea que el comportamiento de los objetos debería estar definido en términos de cómo envía mensajes a otros objetos, además de los resultados devueltos en respuesta a mensajes recibidos, esto último propio de UTDD. Esta práctica se presentó como ***Need-Driven Development (NDD)***. 

El propósito fundamental es resolver un buen diseño orientado a objetos y una separación clara de incumbencias, sobre la base de:
- Mejorar el código con términos de dominio.
- Preservar el encapsulamiento.
- Reducir dependencias.
- Clarificar las interacciones entre clases. 

La diferencia fundamental con el UTDD tradicional, en el que se basa, es que **pretende definir de antemano qué mensajes emitirá el objeto sometido a prueba cuando
reciba un mensaje en particular**. 

Como esto **requiere de otros objetos que puedan recibir a su vez los mensajes emitidos** por el objeto receptor, pero dichos objetos podrían no tener su clase definida en el momento de escribir la prueba, NDD propone implementarlos como **Mock Objects** a partir solamente de la interfaz requerida.

### Discusión sobre pros y contras
Una consecuencia positiva del uso de esta técnica es que, al trabajar sobre la base de protocolos, además definidos en la forma restringida que necesita cada funcionalidad, **se suele llegar a interfaces bien angostas**.

Y como siempre se crea antes la interfaz que la clase, **suelen obtenerse conceptos bien abstractos definidos a nivel de interfaces**.

La misma razón hace que tendamos a escribir **código de pruebas menos acoplado** a implementaciones particulares.

Por otro lado, es innegable que NDD **promueve el ocultamiento de implementación**, ya que impone un protocolo para los objetos receptores, pero no dice cómo implementarlo. 

El principal problema que representa NDD es que **es sensible a las refactorizaciones de los objetos colaboradores**, ya que cuando renombramos métodos, las pruebas dejan de funcionar.

Otra consecuencia, tal vez negativa, es que **resulta costoso tener que crear Mock Objects realistas para todas las interfaces posibles** del objeto a desarrollar. 


## Pruebas de interacción y TDD 
### Pruebas e interfaz de usuario 
Todas las prácticas anteriores (TDD, ATDD, BDD, STDD, NDD) fueron pensadas para especificar, diseñar y probar comportamiento de dominio. No se han planteado automatizar pruebas de interfaz de usuario, de interacción.   

Por que?
-  "No conviene hacer pruebas automatizadas sobre la interfaz de usuario, porque **ésta es muy cambiante y las pruebas se desactualizan con mucha frecuencia**."
-  "Hay que **separar el qué del cómo**, diciendo que el cómo es menos relevante y más cambiante, y por lo tanto no debe ser parte de TDD"
-  Las pruebas de interfaz de usuario **suelen ser muy lentas de ejecutarse**, lo cual las hace poco convenientes en los términos de las barreras tecnológicas a los métodos ágiles
-  Encima, hay cuestiones que sólo las puede probar satisfactoriamente un usuario humano. Por ejemplo, la ubicación de los botones, los colores, etc.

Pero esto está dejando de lado algo fundamental: el valor para el negocio, que se logra indudablemente mediante **el comportamiento, se exhibe y se materializa a través de la interfaz de usuario**.
Ademas, la mayoría de los usuarios reales sólo consideran que la aplicación les sirve cuando la ven a través de su interfaz de usuario

En definitiva, ***no se puede dejar sin probar la interfaz de usuario***. 

El conflicto de TDD con esta forma de trabajo es más bien filosófico: la propia noción de construir algo para luego grabar su ejecución no se lleva bien con la práctica de Test-First, básica de TDD.

### La falta de una visión integral 
Todavía falta, **para considerar a TDD una técnica completa**, que **las pruebas de interacción sobre la interfaz de usuario puedan integrarse a las pruebas de comportamiento**, a nivel de modelo de negocio.

De todas maneras, aun cuando no haya una integración entre ambos tipos de pruebas, **hacerlas por separado es un gran avance**. De hecho, probar la interfaz de usuario sabiendo de antemano que el comportamiento está funcionando correctamente y ha sido probado, es más tranquilizante.

### Limitaciones de las pruebas de interacción 
Las pruebas de interacción automatizadas tienen mala fama, a tal punto que a este problema se le ha dado un nombre: ***“El problema de la prueba frágil”***

Los problemas que suelen presentar las pruebas automatizadas de interacción generadas por grabación, son: 
- **Sensibilidad al comportamiento**: los cambios de comportamiento provocan cambios importantes en la interfaz de usuario, que hacen que las pruebas de interacción dejen de funcionar.
- **Sensibilidad a la interfaz**: aún cambios pequeños a la interfaz de usuario suelen provocar que las pruebas dejen de correr y deban ser cambiadas. 
- **Sensibilidad a los datos**: cuando hay cambios en los datos que se usan para correr la aplicación, los resultados que ésta arroje van a cambiar, lo que hace que haya que generar datos especiales para probar.
- **Sensibilidad al contexto**: igual que con los datos, las pruebas pueden ser sensibles a cambios en dispositivos externos a la aplicación.


## Tipos de pruebas y automatización
### Qué automatizar 
Si partimos de la noción de que las pruebas se hacen para controlar la calidad del producto,podemos clasificarlas en más de una dimensión: 
- **Pruebas de cliente**: explicitan la intención del analista de negocio y hacen las veces de especificaciones ejecutables. 
- **Pruebas de componentes**: definen el diseño del sistema y explicitan la intención del arquitecto; a veces se las llama pruebas de integración técnicas. 
- **Pruebas de unidad**: definen el diseño del código y explicitan la intención deldesarrollador.
- **Pruebas de usabilidad**: definen si el sistema es cómodo de usar (y aprender a usar) para sus usuarios.
- **Pruebas exploratorias**: definen si el sistema es consistente desde el punto de vista del cliente.
- **Pruebas de propiedades**: especifican atributos de calidad, definiendo si el sistema es seguro, escalable, robusto, etc. 

Las de cliente, las de componentes, las de unidad y las de propiedades, se pueden y conviene automatizarlas.  
En cambio, las pruebas de usabilidad y las exploratorias, sólo es posible hacerlas en forma manual. 


## Estudios del uso de TDD en la práctica
### Conclusiones extraídas de la evidencia analizada 
- En cuanto a la calidad externa medida a través de la densidad de defectos encontrados en las pruebas funcionales, se ha reportado una mejora de entre el 40% y el 90%
- En cuanto al tiempo de desarrollo, se ha reportado un mayor tiempo, del entre 15% y el 35%
- Se reporta un descenso en la cantidad de errores introducidos
- Incluso los tiempos de corrección de errores y de cambios muestran descensos interesantes.

Hay también aspectos cualitativos que se analizan en los trabajos analizados. Entre ellos destacan:
- La presión interna de la organización pone en riesgo el uso correcto de TDD, tanto por no comprender la importancia de escribir la cantidad de pruebas necesarias como por la tendencia a abandonar la práctica cuando los cronogramas se vuelven más ajustados.
- Cuando se presentan muchas trabas, humanas, metodológicas o tecnológicas, para hacer TDD, los desarrolladores suelen dejar de lado la práctica en poco tiempo.
- La satisfacción laboral suele ser mayor para los desarrolladores que con TDD pueden ver que las pruebas corren satisfactoriamente.
