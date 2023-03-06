# Factory Pattern

### Clasificacion: Creacional

### Descripcion: 
Proporciona una interfaz para crear objetos en una superclase, mientras permite a las subclases alterar el tipo de objetos que se crearán.

### Problema:
Imagina que estás creando una aplicación de gestión logística. La primera versión de tu aplicación sólo es capaz de manejar el transporte en camión, por lo que la mayor parte de tu código se encuentra dentro de la clase Camión.

Para añadir barcos a la aplicación habría que hacer cambios en toda la base del código. Además, si más tarde decides añadir otro tipo de transporte a la aplicación, probablemente tendrás que volver a hacer todos estos cambios.

### Solución:
![image](https://user-images.githubusercontent.com/86437352/223202756-065f607d-698f-47fe-be89-f5c39572f10d.png)

Ahora puedes sobrescribir el método fábrica en una subclase y cambiar la clase de los productos creados por el método.

### Limitaciones: 
- Las subclases sólo pueden devolver productos de distintos tipos si dichos productos tienen una clase base o interfaz común. 
![image](https://user-images.githubusercontent.com/86437352/223203287-2a9c2314-84df-41b2-97af-9a691fc2da52.png)

- El método fábrica en la clase base debe tener su tipo de retorno declarado como dicha interfaz. El código que utiliza el método fábrica (a menudo denominado código cliente) no encuentra diferencias entre los productos devueltos por varias subclases, y trata a todos los productos como la clase abstracta Transporte.


### Estructura: 
![image](https://user-images.githubusercontent.com/86437352/223203839-31ad19b0-ff85-4cc0-b358-c09194c65e85.png)

### Principios que respeta:
- ***Principio de responsabilidad única***: Puedes mover el código de creación de producto a un lugar del programa, haciendo que el código sea más fácil de mantener.
- ***Principio de abierto/cerrado***: Puedes incorporar nuevos tipos de productos en el programa sin descomponer el código cliente existente.

