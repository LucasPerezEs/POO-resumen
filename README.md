# Programacion orientada a objetos

### Introduccion al paradigma:

La programación orientada a objetos (POO) es un paradigma de programación que se basa en el concepto de clases y objetos . Se utiliza para estructurar un programa de software en piezas simples y reutilizables de planos de código (generalmente llamadas clases), que se utilizan para crear instancias individuales de objetos los cuales envian y reciven mensajes.

   - #### Razones del paradigma:
     -  Mejor manejo de la complejidad
     -  Facilidad de cambios
   
   - #### Pasos para solucionar un problema:
     1. Encontrar objetos
     2. Determinar como deben interactuar los objetos
     3. Implementar el comportamiento de los objetos
   
   - #### Definiciones importantes:
     - **Mensaje**: Es la interaccion entre un objeto que pide un servicio y otro que lo brinda. El objeto que envia se llama **cliente** y el que lo recibe **objeto receptor**
     - **Delegacion**: Cuando un objeto para responder un mensaje envia mensajes a otros objetos esta delegando ese comportamiento
     - **Comportamiento**: Las posibles respuestas a los mensajes recibidos por un objeto
     - **Metodo**: La implementacion de la respuesta de un objeto a un mensaje
 
### Objetos
Es una entidad que puede recibir mensajes, responder a los mismos y enviar mensajes a otros objetos. En resumen decimos que un objeto es una entidad que tiene comportamiento.

#### Caracteristicas de los objetos:
  - **Identidad**: Es lo que distingue un objeto de otro. Por mas que tengan comportamiento igual, la celda 2-3 y la celda 2-5 son dos objetos distintos.
  - **Estado**: Es la situacion en la que se encuentra un objeto. Puede cambiar su estado con el tiempo.
  -  **Comportamiento**: Esta compuesto por las respuestas a los mensajes que recibe el objeto, que a su vez pueden provocar:
	  -  Un cambio de estado en el objeto receptor del mensaje
	  -  La devolucion del estado de un objeto, total o parcialmente
	  -  El envio de un mensaje desde el objeto receptor a otro objeto (delegacion)

### Encapsulamiento
Cada objeto es responsable de responder a los mensajes que recibe, sin que quien le envia el mensaje tenga que saber como lo hace. (Caja negra)

 Esto permite que:
- Pueda haber distintas implementaciones para una misma operacion
- En el futuro podamos cambiar una implementacion por otra sin afectar al cliente

#### **"Tell, don't ask"**
Es un corolario de encapsulamiento que implica que los objetos deben manejar su propio comportamiento sin que nosotros manipulemos su estado desde afuera.

Ejemplo  `celda >> contiene (0)` violaria el encapsulamiento, ya que nosotros conocemos la implementacion interna del objeto.  
La manera de hacerlo es `celda >> estaLibre` ya que de esta manera la implementacion interna seria desconocida para el cliente.

### Polimorfismo
Es la capacidad de respuesta que tienen distintos objetos de responder de maneras diferentes a un mismo mensaje


## Smalltalk
**Smalltalk** es un lenguaje basado en clases, que crea los objetos en el area de memoria dinamica en tiempo de ejecucion. Si bien es compilado, solo hace chequeo de tipos en tiempo de ejecucion.


