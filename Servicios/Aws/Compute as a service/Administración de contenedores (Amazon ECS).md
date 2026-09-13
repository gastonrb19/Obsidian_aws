### Descripción del servicio
Amazon ECS es un servicio integral de orquestación de contenedores que ayuda a iniciar contenedores nuevos. Con Amazon ECS, los contenedores se determinan en una definición de tareas que usted utiliza para ejecutar una tarea individual o una tarea dentro de un servicio. Puede ejecutar sus tareas y servicios en una infraestructura sin servidor administrada por otro servicio de AWS denominado AWS Fargate. De manera alternativa, para tener más control sobre la infraestructura, puede ejecutar sus tareas y servicios en un clúster de instancias de EC2 que usted administre.![[Captura de pantalla 2026-09-08 a las 11.23.14 p. m..png]]

Cuando las instancias de contenedor de Amazon ECS estén en funcionamiento, puede realizar acciones que incluyen, entre otras, las siguientes:
- Lanzar y detener contenedores.
- Obtener el estado del clúster.
- Escalar hacia dentro y hacia fuera.
- Programar la ubicación de los contenedores en el clúster.
- Asignar permisos.
- Cumplir con los requisitos de disponibilidad.
#### ECS
Si elige tener más control ejecutando y administrando sus contenedores en un clúster de instancias de Amazon EC2, también necesitará instalar el agente de contenedores de Amazon ECS en sus instancias de EC2. Tenga en cuenta que una instancia de EC2 con el agente de contenedor instalado suele denominarse instancia de contenedor. Este agente de contenedores es de código abierto y se encarga de informar al servicio Amazon ECS los detalles de la administración del clúster. Puede ejecutar el agente en las AMI de Linux y Windows. Con el agente instalado previamente, también hay una AMI optimizada para ECS disponible.
![[Captura de pantalla 2026-09-08 a las 11.26.27 p. m..png]]
### Costo asociado

### Sub área

### Plataforma

| Nombre/Relación | Descripción de la relación           |
| --------------- | ------------------------------------ |
| [[!Aws]]        | Plataforma que provee el servicio    |
|                 | Plataforma que utiliza el servicio:w |

### Entidades asociadas
- [[!Servicios]]