# Command Pattern

### Clasificacion: Comportamiento

### Descripcion:
Convierte una solicitud en un objeto independiente que contiene toda la información sobre la solicitud. Esta transformación te permite parametrizar los métodos con diferentes solicitudes, retrasar o poner en cola la ejecución de una solicitud y soportar operaciones que no se pueden realizar.

### Problema:
Supongamos que tu tarea actual consiste en crear una barra de herramientas con unos cuantos botones para varias operaciones de un editor de texto.

Creaste una clase Botón muy limpia que puede utilizarse para los botones de la barra de herramientas y también para botones genéricos en diversos diálogos.

Aunque todos estos botones se parecen, se supone que hacen cosas diferentes. La solución más simple consiste en crear cientos de subclases para cada lugar donde se utilice el botón.

Pronto te das cuenta de que esta solución es muy deficiente. En primer lugar, tienes una **enorme cantidad de subclases**, lo cual no supondría un problema si no **corrieras el riesgo de descomponer el código de esas subclases cada vez que modifiques la clase base Botón**.

Y aquí está la parte más desagradable. Algunas operaciones, como copiar/pegar texto, deben ser invocadas desde varios lugares. Por ejemplo, un usuario podría hacer clic en un pequeño botón “Copiar” de la barra de herramientas, o copiar algo a través del menú contextual, o pulsar Ctrl+C en el teclado. 

**Cuando implementas menús contextuales, atajos y otros elementos**, **debes duplicar el código de la operación en muchas clases**, o bien hacer menús dependientes de los botones, lo cual es una opción aún peor.

### Solución
El patrón Command sugiere que los objetos GUI no envíen estas solicitudes directamente. En lugar de ello, debes **extraer todos los detalles de la solicitud**, como el objeto que está siendo invocado, el nombre del método y la lista de argumentos, **y ponerlos dentro de una clase comando separada con un único método que activa esta solicitud**.
![image](https://user-images.githubusercontent.com/86437352/223515009-b353d814-a566-4dec-983a-3bb579e8ec8f.png)

El siguiente paso es hacer que tus comandos implementen la misma interfaz. Normalmente tiene un único método de ejecución que no acepta parámetros.

Esta interfaz te permite utilizar varios comandos con el mismo emisor de la solicitud, sin acoplarla a clases concretas de comandos. Adicionalmente, ahora puedes cambiar objetos de comando vinculados al emisor, cambiando efectivamente el comportamiento del emisor durante el tiempo de ejecución.

![image](https://user-images.githubusercontent.com/86437352/223515644-4fda02db-d4a2-46a1-acfc-e04a92d8040e.png)

Tras aplicar el patrón Command, ya no necesitamos todas esas subclases de botón para implementar varios comportamientos de clic. Basta con colocar un único campo dentro de la clase base Botón que almacene una referencia a un objeto de comando y haga que el botón ejecute ese comando en un clic.

### Principios que respeta:
- ***Principio de responsabilidad única***: Puedes desacoplar las clases que invocan operaciones de las que realizan esas operaciones.
- ***Principio de abierto/cerrado***: Puedes introducir nuevos comandos en la aplicación sin descomponer el código cliente existente.
