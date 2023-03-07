# Proxy Pattern

### Clasificacion: Estructural

### Descripcion:
Permite proporcionar un sustituto o marcador de posición para otro objeto. Un proxy controla el acceso al objeto original, permitiéndote hacer algo antes o después de que la solicitud llegue al objeto original.

### Problema:
¿Por qué querrías controlar el acceso a un objeto? Imagina que tienes un objeto enorme que consume una gran cantidad de recursos del sistema. Lo necesitas de vez en cuando, pero no siempre.

Puedes llevar a cabo una implementación diferida, es decir, crear este objeto sólo cuando sea realmente necesario. Todos los clientes del objeto tendrán que ejecutar algún código de inicialización diferida. Lamentablemente, esto seguramente generará una gran cantidad de código duplicado.

### Solución:
El patrón Proxy sugiere que crees una nueva clase proxy con la misma interfaz que un objeto de servicio original. Después actualizas tu aplicación para que pase el objeto proxy a todos los clientes del objeto original. Al recibir una solicitud de un cliente, el proxy crea un objeto de servicio real y le delega todo el trabajo.
![image](https://user-images.githubusercontent.com/86437352/223518126-48782548-e3ae-4022-9f04-ac7505ef798d.png)

Pero, ¿cuál es la ventaja? Si necesitas ejecutar algo antes o después de la lógica primaria de la clase, el proxy te permite hacerlo sin cambiar esa clase. Ya que el proxy implementa la misma interfaz que la clase original, puede pasarse a cualquier cliente que espere un objeto de servicio real.

### Estructura:
![image](https://user-images.githubusercontent.com/86437352/223518716-7f50a54b-c996-4ef2-aa10-3d25a5200bea.png)

### Principios que respeta:
- ***Principio de abierto/cerrado***: Puedes introducir nuevos proxies sin cambiar el servicio o los clientes.
