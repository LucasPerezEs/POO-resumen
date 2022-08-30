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
     
### Clases
Conjuntos de objetos que, por lo menos, tienen el mismo comportamiento (entienden los mismos mensajes y responden de la misma manera).
Todos los objetos son instancias de clases.
 
### Objetos
Es una entidad que puede recibir mensajes, responder a los mismos y enviar mensajes a otros objetos. En resumen decimos que un objeto es una entidad que tiene comportamiento y que solo existe en tiempo de ejecucion.

#### Caracteristicas de los objetos:
  - **Identidad**: Es lo que distingue un objeto de otro. Por mas que tengan comportamiento igual, la celda 2-3 y la celda 2-5 son dos objetos distintos.
  - **Estado**: Es la situacion en la que se encuentra un objeto. Puede cambiar su estado con el tiempo.
  -  **Comportamiento**: Esta compuesto por las respuestas a los mensajes que recibe el objeto, que a su vez pueden provocar:
	  -  Un cambio de estado en el objeto receptor del mensaje
	  -  La devolucion del estado de un objeto, total o parcialmente
	  -  El envio de un mensaje desde el objeto receptor a otro objeto (delegacion).
  - **Atributos**: Variables internas del objeto que sirven para almacenar parte del estado del mismo

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

### Caracteristicas del lenguaje
- Todo dentro del lenguaje es un objeto (numeros, cadenas, vectores, etc).
- Las variables son referencias a objetos y no tienen tipo, los objetos si.
- Smalltalk compila los programas, pero no muestra error si operamos con variables que contienen referencias a objetos de tipos incompatibles, ya que estos solo existen en tiempo de ejecucion
- Tampoco muestra error si enviamos mensajes a objetos que no los van a comprender, por el mismo motivo.
- El lenguaje tiene recoleccion automatica de basura.
- Las **variables locales** se declaran entre placas. `| variable1 variable2 |`
- Las sentencias terminan con punto. "."
- Los comentarios van entre comillas. `"Esto es un comentario"`
- La asignacion es con `:=` y la comparacion con `=`.

### Creacion de objetos
`celda23 := Celda new.`
La creacion del objeto que representa la celda 2-3 se haria enviando el mensaje **new** a la clase **Celda**.  

**IMPORTANTE**: `"celda23"` **_no_ es un objeto**, es una variable que referencia a un objeto celda. Algo asi como un puntero a un objeto.

### Implementacion de metodos
```
estaLibre  
	^ (contenido = 0 )
```

### Bloques de codigo
- Es un objeto asociado a la clase *BlockClosure*
- Se crea un bloque de codigo con dos corchetes `[   ]`.
- Para evaluar el bloque de codigo, se manda el mensaje `value` 	Ejemplo) `[ 2 + 2 ] value.` devuelve 4.
- Puede tomar argumentos al principio de la siguiente manera: `[ :x | x+2 ] value: 4.` devuelve 6.
- Para mas de un argumento, hacemos `[ :x :y | x + y ] value: 3 value: 5.` devuelve 8.
- Podemos almacenar un bloque de codigo en una variable para evaluarlo despues:
	```
	|miBloque|
	miBloque := [ :x :y | x + y ].
	```
  Para luego poder evaluarlo con `miBloque value: 3 value: 5.`

### Estructuras de control

### If
Reciben como parametro un bloque de codigo y se realizan mediante el envio de mensajes, hay 3 tipos:
- **ifTrue** que ejecuta el codigo solo si la condicion es verdadera. `(1 > 2) ifTrue: [ Transcript show: 'Es mayor'].`
- **ifFalse** que ejecuta el codigo solo si la condicion es falsa. `(1 > 2) ifFalse: [Transcript show: 'Es menor'].`
- **ifTrue ifFalse** que se asemeja al famoso If/Else. 
	```
	(1 > 2)
		ifTrue: [Transcript show: 'Es Mayor']
		ifFalse: [Transcript show: 'Es menor'].
	```
 ### Iteracion
 - **timesRepeat** mensaje que entienden las instancias de la clase integer. 
 ```
 n := 1.
 10 timesRepeat: [ n := n * 2 ].
 ```
 - **whileTrue** mensaje entendido por los bloques de codigo.
 ```
 n := 1.
 i := 0.
 [ i < 10] whileTrue: [
 	n := n * 2.
	i := i + 1.
].
```
- **do**: Iterador que entienden todas las colecciones como Array, OrderedCollection, etc
`numeros do: [ :numero | Transcript show: numero ].`

### Arreglos
- **Array**: Para crearlo le enviamos el mensaje **new** que indica la cantidad maxima de elementos del array. Para insertar elementos, el array entiende el mensaje `at: put:`. Su tamanio es fijo y no se puede redimensionar.
```
numeros := Array new: 5.
numeros at: 1 put: 3.
numeros at: 2 put: 1/2.
numeros at: 3 put: 'HOLA'.
numeros do: [ :numero | Transcript show: numero ].
```
- **OrderedCollection**: Muy similar al array pero el tamanio es dinamico. Para agregar elementos se envia el mensaje `add`
```
numeros := OrderedCollection new.
numeros add: 5.
numeros add: 1/2.
numeros add: 'HOLA'.
numeros do: [ :numero | Transcript show: numero ].
```
