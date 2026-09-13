### Descripción del servicio
Con Amazon RDS, puede deshacerse de parte del trabajo que no está relacionado con crear y administrar una base de datos. Puede centrarse en las tareas que diferencian a su aplicación, en lugar de centrarse en las tareas relacionadas con la infraestructura, como el aprovisionamiento, la aplicación de parches, el escalado y la restauración.  
  
Amazon RDS admite la mayoría de los RDBMS populares, que abarcan desde opciones comerciales hasta opciones de código abierto e incluso una opción específica de AWS. Entre los motores de Amazon RDS compatibles se incluyen los siguientes:

- **Comercial:** Oracle, SQL Server
    
- **Código abierto:** MySQL, PostgreSQL, MariaDB
    
- **Nativo en la nube:** Aurora

#### Lanzamiento multiple en diferentes zonas de disponibilidad A-Z
Al realizar el seguimiento de las buenas prácticas recomendadas para los servicios de almacenamiento hay que considerar realizar el aprovisionamiento de la instancia dentro de al menos 2 zonas de disponibilidad, ya que ante una eventual caída del servicio este balanceador dirigirá la conexión hacía la instancia disponible. 

#### Subsistema 
Debajo de la instancia de base de datos hay una instancia de EC2. Sin embargo, esta instancia se administra a través de la consola de Amazon RDS en lugar de la consola de Amazon EC2. Al crear la instancia de base de datos, elige el tipo y el tamaño de la instancia. La clase de instancia de base de datos que elija influye en la capacidad de procesamiento y la memoria de la que dispone.
### Costo asociado

### Sub área

### Plataforma

| Nombre/Relación | Descripción de la relación           |
| --------------- | ------------------------------------ |
| [[!Aws]]        | Plataforma que provee el servicio    |
|                 | Plataforma que utiliza el servicio:w |

### Entidades asociadas
- [[!Servicios]]