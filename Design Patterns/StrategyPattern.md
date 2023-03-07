# Strategy Pattern

### Clasificacion: Comportamiento

### Descripcion: 
Permite definir una familia de algoritmos, colocar cada uno de ellos en una clase separada y hacer sus objetos intercambiables.

### Problema:
Un día decidiste crear una aplicación de navegación para viajeros ocasionales. Una de las funciones más solicitadas para la aplicación era la planificación automática de rutas.

La primera versión de la aplicación sólo podía generar las rutas sobre carreteras. En la siguiente actualización, añadiste una opción para crear rutas a pie. Después, añadiste otra opción para permitir a las personas utilizar el transporte público en sus rutas. Más tarde planeaste añadir la generación de rutas para ciclistas, y más tarde, otra opción para trazar rutas por todas las atracciones turísticas de una ciudad.

Cada vez que añadías un nuevo algoritmo de enrutamiento, la clase principal del navegador doblaba su tamaño. Cualquier cambio en alguno de los algoritmos afectaba a toda la clase, aumentando las probabilidades de crear un error en un código ya funcional.

### Solución:
El patrón Strategy sugiere que tomes esa clase que hace algo específico de muchas formas diferentes y extraigas todos esos algoritmos para colocarlos en clases separadas llamadas ***estrategias***.

La clase original, llamada ***contexto***, debe tener un campo para almacenar una referencia a una de las estrategias. El contexto delega el trabajo a un objeto de estrategia vinculado en lugar de ejecutarlo por su cuenta.

La clase contexto no es responsable de seleccionar un algoritmo adecuado para la tarea. En lugar de eso, el cliente pasa la estrategia deseada a la clase contexto. 

De esta forma, el contexto se vuelve independiente de las estrategias concretas, así que puedes añadir nuevos algoritmos o modificar los existentes sin cambiar el código de la clase contexto o de otras estrategias.

La clase tiene un método para cambiar la estrategia activa de enrutamiento, de modo que sus clientes, como los botones en la interfaz de usuario, pueden sustituir el comportamiento seleccionado de enrutamiento por otro.

![image](https://user-images.githubusercontent.com/86437352/223534247-7e70d46b-9931-486e-808c-c7a36923992e.png)

### Estructura:
![image](https://user-images.githubusercontent.com/86437352/223534625-48558e8f-85cc-49b6-85c6-bd207edd2f3e.png)

### Principios que respeta:
- ***Principio de abierto/cerrado***: Puedes introducir nuevas estrategias sin tener que cambiar el contexto.


