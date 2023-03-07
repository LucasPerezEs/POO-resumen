# Decorator Pattern

### Clasificacion: Estructural

### Descripcion: 
Permite añadir funcionalidades a objetos colocando estos objetos dentro de objetos encapsuladores especiales que contienen estas funcionalidades.

### Problema: 
Imagina que estás trabajando en una biblioteca de notificaciones que permite a otros programas notificar a sus usuarios acerca de eventos importantes.

La versión inicial de la biblioteca se basaba en la clase Notificador que solo contaba con unos cuantos campos, un constructor y un único método send. El método podía aceptar un argumento de mensaje de un cliente y enviar el mensaje a una lista de correos electrónicos que se pasaban a la clase notificadora a través de su constructor. 

En cierto momento te das cuenta de que los usuarios de la biblioteca esperan algo más que unas simples notificaciones por correo. A muchos de ellos les gustaría recibir mensajes SMS, notificaciones por Facebook o por Slack.

![image](https://user-images.githubusercontent.com/86437352/223552888-de42d0ee-12c0-4b39-81a7-836be47e680c.png)

Extendiste la clase Notificador y metiste los métodos adicionales de notificación dentro de nuevas subclases. 

Pero entonces alguien te hace una pregunta razonable: “¿Por qué no se pueden utilizar varios tipos de notificación al mismo tiempo? Si tu casa está en llamas, probablemente quieras que te informen a través de todos los canales”.

Intentaste solucionar ese problema creando subclases especiales que combinaban varios métodos de notificación dentro de una clase. Sin embargo, enseguida resultó evidente que esta solución inflaría el código en gran medida, no sólo el de la biblioteca, sino también el código cliente.

![image](https://user-images.githubusercontent.com/86437352/223553779-4388c440-2087-4247-a9fd-0dd4b92d3774.png)

### Solución:
Una de las formas de superar estas limitaciones es empleando la Agregación o la Composición en lugar de la Herencia. 

Con esta nueva solución puedes sustituir fácilmente el objeto “ayudante” vinculado por otro, cambiando el comportamiento del contenedor durante el tiempo de ejecución. Un objeto puede utilizar el comportamiento de varias clases con referencias a varios objetos, delegándoles todo tipo de tareas. 

***“Wrapper”*** (envoltorio, en inglés) es el sobrenombre alternativo del patrón Decorator, que expresa claramente su idea principal. Un wrapper es un objeto que puede vincularse con un objeto objetivo. El wrapper contiene el mismo grupo de métodos que el objetivo y le delega todas las solicitudes que recibe. No obstante, el wrapper puede alterar el resultado haciendo algo antes o después de pasar la solicitud al objetivo.

El wrapper implementa la misma interfaz que el objeto envuelto. Éste es el motivo por el que, desde la perspectiva del cliente, estos objetos son idénticos. Ademas, esto permitirá envolver un objeto en varios wrappers, añadiéndole el comportamiento combinado de todos ellos.

![image](https://user-images.githubusercontent.com/86437352/223558857-f221e12c-38ba-49a8-9c94-730dbf5ff16e.png)

El código cliente debe envolver un objeto notificador básico dentro de un grupo de decoradores que satisfagan las preferencias del cliente. Los objetos resultantes se estructurarán como una pila.

![image](https://user-images.githubusercontent.com/86437352/223560501-e653a922-614c-47db-adaf-712f386a9d8a.png)

El último decorador de la pila será el objeto con el que el cliente trabaja. 

### Estructura:
![image](https://user-images.githubusercontent.com/86437352/223560821-edc334d1-73f3-44b1-927f-e849e1e7bd32.png)

### Principios que respeta:
- ***Principio de responsabilidad única***: Puedes dividir una clase monolítica que implementa muchas variantes posibles de comportamiento, en varias clases más pequeñas.



