# Singleton Pattern

### Clasificacion: Creacional

### Descripcion:
Nos permite asegurarnos de que una clase tenga una única instancia, a la vez que proporciona un punto de acceso global a dicha instancia.

### Problema:
El patrón Singleton resuelve dos problemas al mismo tiempo, **vulnerando el Principio de responsabilidad única**:

1) ***Garantizar que una clase tenga una única instancia***: El motivo más habitual es controlar el acceso a algún recurso compartido, por ejemplo, una base de datos o un archivo. Funciona así: imagina que has creado un objeto y al cabo de un tiempo decides crear otro nuevo. En lugar de recibir un objeto nuevo, obtendrás el que ya habías creado.

2) ***Proporcionar un punto de acceso global a dicha instancia***: Al igual que una variable global, el patrón Singleton nos permite acceder a un objeto desde cualquier parte del programa. No obstante, también evita que otro código sobreescriba esa instancia.

### Solución:
- Hacer privado el constructor por defecto para evitar que otros objetos utilicen el operador 'new' con la clase Singleton.
- Crear un método de creación estático que actúe como constructor. Tras bambalinas, este método invoca al constructor privado para crear un objeto y lo guarda en un campo estático. Las siguientes llamadas a este método devuelven el objeto almacenado en caché.

### Estructura:

![image](https://user-images.githubusercontent.com/86437352/223207912-e896f525-c24d-4c35-986a-8130d9f5f19f.png)
