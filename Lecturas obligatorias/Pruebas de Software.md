# Pruebas de Software - Resumen

## Que probamos

### Verificacion y Validacion
Hay pruebas centradas en la verificación y otras centradas en la validación.  
- La **`verificación`** tiene que ver con controlar que hayamos construido el producto tal como
pretendimos construirlo.
- La **`validación`**, en cambio, controla que hayamos construido el
producto que nuestro cliente quería.

### Funcionalidades y atributos de calidad
Llamamos **`pruebas funcionales`** a las pruebas centradas en probar funcionalidades, cosas que el programa debe hacer.  
Por ejemplo, *Si intento colocar una ficha en una celda ocupada, el programa debe impedirlo*.

Pero en ocasiones ocurre que debemos probar características del sistema que no son
funcionales. Decimos que estas son **`pruebas de atributos de calidad`**.  
Por ejemplo, *El tiempo de respuesta del juego no puede ser superior a 1 segundo*.  

Hay muchos tipos de pruebas de atributos de calidad, entre ellos: Pruebas de compatibilidad, Pruebas de rendimiento, Pruebas de resistencia o de estrés, Pruebas de seguridad, Pruebas de recuperación, Pruebas de instalación, etc.

## Alcance de las pruebas

### Alcance de las pruebas de verificación (o técnicas)
- Las **`pruebas unitarias`** verifican pequeñas porciones de código. Se trata de pruebas que ejecutan los programadores para ver que lo que acaban
de escribir hace lo que ellos pretendían.
- Las **`pruebas de integración`**, en cambio, prueban que varias porciones de código, trabajando
en conjunto, hacen lo que pretendíamos.

Caracteristicas: 
- Ambos tipos de pruebas son pasibles de ser automatizadas.
- También, en ambos casos, las pruebas de verificación se pueden – y se suelen – escribir antes
del código que prueban (TDD)
- La ventaja de las pruebas unitarias está en que permiten aislarse del conjunto del sistema y
analizar que una pequeña porción de código se comporta como se espera.
- Las pruebas de integración no siempre prueban el sistema como un todo. A veces prueban
también partes del mismo que se quieren aislar de otras.

Las pruebas de verificación podrían ser de caja negra o de caja blanca.
Decimos que una prueba es de **`caja negra`** cuando la ejecutamos sin mirar el código que
estamos probando.  
Cuando, en cambio, analizamos el código durante la prueba, decimos que es una prueba de **`caja blanca`**.   
En general, se prefiere hacer pruebas de caja negra, precisamente porque se desea probar el funcionamiento y no verificar la calidad del código.

### Alcance de las pruebas de validación (o de usuarios)
- En general, se suele trabajar con pruebas de aceptación diseñadas por usuarios pero que ejecuta el equipo de desarrollo. Estas pruebas, se suelen
denominar **`pruebas de aceptación de usuarios (UAT18)`**.  
- Si las pruebas las hacemos en un entorno controlado por el equipo de desarrollo, las llamamos
**`pruebas alfa`**. 
- Si, en cambio, el producto se deja a disposición del cliente para que lo pruebe
en su entorno, las llamamos **`pruebas beta`**.

Todas estas pruebas que hemos mencionado suponen que ejecutamos el sistema completo, pero hay ocasiones en que deseamos probar solamente
comportamiento, pero sin interfaz de usuario. las denominamos **`pruebas de comportamiento`**.

### Pruebas en producción
Se puede también poner el sistema en producción y esperar a ver qué errores
surgen o qué problemas encuentran los usuarios. A esto lo llamamos realizar las **`pruebas en
producción`**. En las aplicaciones en que los errores no causen grandes riesgos, podría ser
una opción.

### La pirámide de pruebas y sus razones

![image](https://user-images.githubusercontent.com/86437352/191120211-696eff53-b1cb-4cf3-a3b3-a3d4a92675d2.png)

## Roles del desarrollo ante las pruebas

### Visiones Tradicionales
- La visión tradicional sostiene que debe haber personas con el rol de **`programadores`** y otras con el rol de **`testers`**, quienes ejecutan las
pruebas y se aseguran que el producto llegue sin errores a los clientes y usuarios.  
- Se basa en la noción administrativa de control cruzado por contraposición de intereses, que hace que el que realiza
un trabajo no puede ser el mismo que lo controla.

### La Vision Agil
- Puso en cuestión la noción de control cruzado con contraposición de intereses.
- Varios métodos ágiles, entre ellos Extreme Programming y Scrum, plantearon que
todo el equipo de desarrollo debe trabajar de consuno y en aras de entregar un producto de
calidad. Por lo tanto, **la responsabilidad por entregar un producto de calidad y sin errores pasó
a ser de todo el equipo de desarrollo (programadores y testers)**.
- Lo que sí ocurre en la vida real es que algunos equipos separan los roles de programador y
tester, pero trabajan en el mismo equipo.

### Pruebas automatizadas: quién las desarrolla
- Las **pruebas unitarias** son pruebas de programador, así que sin duda las deben escribir los
programadores y ejecutarlas ellos mismos.
- Las **pruebas de integración** técnicas también son pruebas de programador: conviene que las
escriban los programadores y que las ejecuten sobre servidores de integración.
- Las **pruebas de comportamiento** están a mitad de camino entre pruebas de programadores y
pruebas de testers. Por lo tanto, cualquiera de los dos roles podría desarrollarlas.
- Con las **UAT automatizadas** en principio, se pretende que las escriban usuarios o analistas de negocio. Si esto no se consiguiera, las
podrían escribir los testers, pero es imperativo validarlas con los usuarios.


## Pruebas y desarrollo

### Cuándo probamos
Hoy en día, con el surgimiento de ciclos de flujo continuo, las pruebas son continuas a lo largo de todo el desarrollo.   
Dada vez que se incorporan características a un programa, podemos provocar que dejen de funcionar cosas que ya habían sido probadas y entregadas: esto es lo que se llama una **`regresión`**.  
Para evitarlas, se ejecutan cada tanto, **`pruebas de regresión`**, que no es otra cosa que ejecutar las pruebas de todo el sistema a intervalos regulares.

### Ventajas de la automatización
- Nos independizamos del factor humano.
- Es más fácil repetir las mismas pruebas, aplicable a regresiones, debugging y errores provenientes del sistema ya en producción.
- Sirven como herramienta de comunicación, minimizando las ambigüedades.

### Tipos de pruebas y automatización
![image](https://user-images.githubusercontent.com/86437352/191127424-84b55704-4500-4c8e-aeb9-e5c178ae4bc1.png)

### TDD
Básicamente, incluye tres sub-prácticas:
- **Automatización**: las pruebas del programa deben ser hechas en código, y con la sola ejecución del código de pruebas debemos saber si lo que estamos probando funciona bien o mal.
- **Test-First**: las pruebas se escriben antes del propio código a probar.
- **Refactorización posterior**: para mantener la calidad del código, se lo cambia sin
cambiar la funcionalidad, manteniendo las pruebas como reaseguro.

**Ciclo del TDD**:  
![image](https://user-images.githubusercontent.com/86437352/191128877-d5c2add6-edc5-4812-87f7-b5d752e818d4.png)
