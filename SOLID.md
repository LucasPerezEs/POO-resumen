## Principios S.O.L.I.D

> ***Principios de Diseño:*** Conjunto de reglas que favorecen y/o fomentan la escritura de codigo extensible y mantenible, minimizando los posibles codigos afectados.

Algunos ejemplos: GRASP, Tell don't ask, Don't repeat yourself, **SOLID**.

## SRP: Principio de Responsabilidad Unica
- **"A module should only be responsible to one, and only one, actor"**
- Una clase solo debe tener una unica razon para cambiar, siendo esta un cambio de requerimiento.

Ejemplo:  

**Problema:**  
La clase empleado tiene mas de una razon de cambio. Por ejemplo, si se cambia la base de datos donde se guardan los empleados, o se cambia la forma de calcular salarios.

![image](https://user-images.githubusercontent.com/86437352/197410445-7fdabcd2-f10d-4c04-95da-2e83ca19596d.png)

**Solucion:** 
Crear mas clases para cada responsabilidad

![image](https://user-images.githubusercontent.com/86437352/197410555-128ba382-c570-4fee-9608-4cb7a380736b.png)


## OCP: Principio de abierto/cerrado
- **"Las clases deben estar abiertas para la extension pero cerradas para su modificacion"**
- Se debe poder cambiar el comportamiento sin modificar el codigo ya existente.

Ejemplo: 

![image](https://user-images.githubusercontent.com/86437352/197412064-d52c1047-8b2e-4dbe-a0b6-3702c227da8e.png)

**Problema:**  
Se ve claro que si quiero agregar una figura Triangulo, debo modificar todo el codigo.

**Solucion:**  
Se puede lograr utilizando herencia o delegacion

![image](https://user-images.githubusercontent.com/86437352/197412611-80c9ac59-7965-4319-b5aa-9c6be5177d2c.png)


## LSP: Principio de Sustitucion de Liskov
- **"Las clases heredadas deben poder ser utilizadas a traves de su clase madre sin necesidad de que el usuario sepa la diferencia"**
- Se debe cumplir la relacion "es un" al aplicar herencia

Ejemplo: 

![image](https://user-images.githubusercontent.com/86437352/197414479-fcaee7c8-4008-40b0-90e9-0c4a44f4944b.png)

## ISP: Principio de Segregacion de la Interfaz
- **"Los clientes no deben ser forzados a depender de metodos que no utilizan"**
- Muchas interfaces especificas son mejores que una interfaz gigante general.
- Es necesario aplicarlo cuando se tiene una clase con varios metodos, de los cuales solo me interesan algunos.

Ejemplo: 

**Problema:**  
Tanto la impresora como el escaner y la fotocopiadora tienen metodos que no deberian tener, porque implementan una interfaz general en comun.

![image](https://user-images.githubusercontent.com/86437352/197414782-6178e5d7-7244-4be7-88ad-cc19d6da8502.png)

**Solucion:**  
![image](https://user-images.githubusercontent.com/86437352/197414963-36262981-aa06-44fb-ad43-34f3786a1301.png)


## DIP: Principio de Inversion de Dependencia
- **"Los modulos de alto nivel no deben depender de los de bajo nivel, ambos deben depender de las abstracciones"**
- Las abstracciones no deben depender de los detalles/implementaciones, los detalles/implementaciones deben depender de las abstracciones.

Ejemplo:

**Problema:** 
Hay un modulo de alto nivel (Facturador) que depende de bajo nivel (una base de datos). Facturador tiene como variable a RepositorioProducto.

![image](https://user-images.githubusercontent.com/86437352/197422066-900336d7-a6b7-4295-97b1-b323bfd14700.png)

**Solucion:** 
Creamos una interfaz que sea implementada por RepositorioProducto, y mediante la inyeccion de dependencias, hacemos que Facturador no tenga a RepositorioProducto como parametro, sino que en el constructor se le pase un objeto que implemente la interfaz Repositorio. De esta forma podemos hacer mejor testing con el uso de mocks, stubs, etc.

![image](https://user-images.githubusercontent.com/86437352/197422207-797cc985-b096-468d-bbbc-834083e43289.png)


