# Abstract Factory Pattern

### Clasificacion: Creacional

### Descripcion: 
Nos permite producir familias de objetos relacionados sin especificar sus clases concretas.

### Problema:
Imagina que estás creando un simulador de tienda de muebles. Tu código está compuesto por clases que representan lo siguiente:

Una familia de productos relacionados, digamos: Silla + Sofá + Mesilla.

Algunas variantes de esta familia. Por ejemplo, los productos Silla + Sofá + Mesilla están disponibles en estas variantes: Moderna, Victoriana, ArtDecó.

![image](https://user-images.githubusercontent.com/86437352/223204778-fbda66b6-7892-447b-901d-d22f36b5c8fd.png)

Necesitamos una forma de crear objetos individuales de mobiliario para que combinen con otros objetos de la misma familia. Además, no queremos cambiar el código existente al añadir al programa nuevos productos o familias de productos. 


### Solución:
Lo primero que sugiere el patrón Abstract Factory es que declaremos de forma explícita interfaces para cada producto diferente de la familia de productos (por ejemplo, silla, sofá o mesilla).

Después podemos hacer que todas las variantes de los productos sigan esas interfaces.
![image](https://user-images.githubusercontent.com/86437352/223205615-3d663194-f2c4-4ed7-9084-581a5ba1b61d.png)

El siguiente paso consiste en declarar la Fábrica abstracta: una interfaz con una lista de métodos de creación para todos los productos que son parte de la familia de productos (por ejemplo, crearSilla, crearSofá y crearMesilla). Estos métodos deben devolver productos abstractos representados por las interfaces que extrajimos previamente: Silla, Sofá, Mesilla, etc.

![image](https://user-images.githubusercontent.com/86437352/223205779-ed9baaea-b7c3-453e-af9a-587c1dccd6f3.png)

El código cliente tiene que funcionar con fábricas y productos a través de sus respectivas interfaces abstractas.

### Principios que respeta:
- ***Principio de responsabilidad única***: Puedes mover el código de creación de productos a un solo lugar, haciendo que el código sea más fácil de mantener.
- ***Principio de abierto/cerrado***: Puedes introducir nuevas variantes de productos sin descomponer el código cliente existente.
