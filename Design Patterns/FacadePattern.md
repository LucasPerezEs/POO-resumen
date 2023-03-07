# Facade Pattern

### Clasificacion: Estructural

### Descripcion:
Proporciona una interfaz simplificada a una biblioteca, un framework o cualquier otro grupo complejo de clases.

### Problema:
Imagina que debes lograr que tu código trabaje con un amplio grupo de objetos que pertenecen a una sofisticada biblioteca o framework. Normalmente, debes inicializar todos esos objetos, llevar un registro de las dependencias, ejecutar los métodos en el orden correcto y así sucesivamente.

Como resultado, la lógica de negocio de tus clases se vería estrechamente acoplada a los detalles de implementación de las clases de terceros, haciéndola difícil de comprender y mantener.

### Solución:
Una fachada es una clase que proporciona una **interfaz simple a un subsistema complejo** que contiene muchas partes móviles. Una fachada puede proporcionar una funcionalidad limitada en comparación con trabajar directamente con el subsistema. Sin embargo, **tan solo incluye las funciones realmente importantes para los clientes**.

### Estructura:
![image](https://user-images.githubusercontent.com/86437352/223521964-eaccc112-5737-43e7-a909-a9cdc9c3d245.png)

