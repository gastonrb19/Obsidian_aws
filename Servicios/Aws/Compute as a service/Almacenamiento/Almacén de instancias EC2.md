### Descripción del servicio
Un almacén de instancias de Amazon Elastic Compute Cloud (Amazon EC2) proporciona almacenamiento temporal a nivel de bloques para una instancia. Este almacenamiento se encuentra en discos que están conectados físicamente al equipo host. Esto vincula el ciclo de vida de los datos con el de la instancia de EC2. Si elimina la instancia, también se elimina el almacén de instancias, por lo que el almacén de instancias se considera un almacenamiento efímero. Obtenga más información al respecto en la documentación de Amazon EC2 que se encuentra en la sección de recursos al final de esta lección.
![[Captura de pantalla 2026-09-10 a las 9.47.55 p. m..png]]
El almacén de instancias es ideal si aloja aplicaciones que replican datos en otras instancias de EC2, como los clústeres de Hadoop. Para estas cargas de trabajo basadas en clústeres, contar con la velocidad de los volúmenes conectados localmente y la resiliencia de los datos replicados lo ayuda a lograr una distribución de datos de alto rendimiento. Este tipo de almacenamiento también es ideal para almacenar temporalmente información que cambia con frecuencia, como búferes, memorias caché, datos de pruebas y otro contenido temporal.
### Costo asociado

### Sub área

### Plataforma

| Nombre/Relación | Descripción de la relación           |
| --------------- | ------------------------------------ |
|                 | Plataforma que provee el servicio    |
|                 | Plataforma que utiliza el servicio:w |

### Entidades asociadas
- [[!Servicios]]