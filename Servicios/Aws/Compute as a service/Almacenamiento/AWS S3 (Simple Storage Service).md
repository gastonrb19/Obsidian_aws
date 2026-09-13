### Descripción del servicio
El **almacenamiento de objetos**, como AWS S3, trata los datos como objetos discretos con metadatos e identificadores únicos. Por tanto, es perfecto para datos no estructurados a gran escala, como archivos multimedia, copias de seguridad y contenido web estático, y ofrece una escalabilidad y durabilidad excelentes.

A diferencia de Amazon EBS, Amazon Simple Storage Service (Amazon S3) es una solución de almacenamiento independiente que no está vinculada a la computación. Con Amazon S3, puede recuperar sus datos desde cualquier lugar de la web. Si alguna vez utilizó un servicio de almacenamiento en línea para realizar copias de seguridad de los datos de su máquina local, lo más probable es que haya utilizado un servicio similar a Amazon S3. La gran diferencia entre esos servicios de almacenamiento en línea y Amazon S3 es el tipo de almacenamiento.  
  
Amazon S3 es un servicio de almacenamiento de objetos y este tipo de servicio almacena los datos en una estructura plana. Un objeto es un archivo combinado con metadatos y puede almacenar la cantidad de estos objetos que desee. Todas las características del almacenamiento de objetos también son características de Amazon S3.

En Amazon S3, los objetos se almacenan en contenedores denominados buckets. No puede cargar un objeto, ni una sola foto, en Amazon S3 sin crear primero un bucket. Cuando almacena un objeto en un bucket, la combinación de nombre de bucket, clave e ID de versión identifica de forma única al objeto.
**Cuando crea un bucket, especifica, como mínimo, dos detalles: el nombre del bucket y la región de AWS en la que desea que resida el bucket.**

#### Casos de uso de amazon S3
- *Copias de seguridad y almacenamiento*: Amazon S3 es un lugar natural para realizar copias de seguridad de los archivos, ya que es altamente redundante. Como se mencionó en la lección anterior, AWS almacena las instantáneas de EBS en Amazon S3 para aprovechar su alta disponibilidad.
- *Alojamiento de medios*: Dado que puede almacenar objetos ilimitados y cada objeto individual puede tener hasta 5 TB, Amazon S3 es un lugar ideal para alojar cargas de video, fotos y música. 
- *Entrega de software*: Puede usar Amazon S3 a fin de alojar las aplicaciones de software para que los clientes puedan descargarlas.
- *Lagos de datos*: Amazon S3 es una base óptima para un lago de datos debido a su escalabilidad prácticamente ilimitada. Puede aumentar el almacenamiento de gigabytes a petabytes de contenido y pagar solo por lo que usa. 
- *Sitios web estáticos*: Puede configurar su bucket de S3 para alojar un sitio web estático de HTML, CSS y scripts del lado del cliente.
- *Contenido estático:* Gracias al escalado ilimitado, la compatibilidad con archivos de gran tamaño y el hecho de que puede acceder a cualquier objeto a través de la web en cualquier momento, Amazon S3 es el lugar perfecto para almacenar contenido estático.
#### Clases de almacenamiento Amazon S3
Cuando carga un objeto a Amazon S3 y no especifica la clase de almacenamiento, lo carga a la clase de almacenamiento predeterminada, que a menudo se conoce como almacenamiento estándar. En las lecciones anteriores, aprendió acerca de la clase de almacenamiento estándar predeterminada de Amazon S3.  
Las clases de almacenamiento de Amazon S3 le permiten cambiar el nivel de almacenamiento cuando cambian las características de los datos. Por ejemplo, si accede a sus fotos antiguas con poca frecuencia, es posible que desee cambiar la clase de almacenamiento de las fotos para ahorrar costos.

|**Clase de almacenamiento**|**Descripción**|
|---|---|
|**S3 Standard**|Se considera un almacenamiento de uso general para aplicaciones en la nube, sitios web dinámicos, distribución de contenido, aplicaciones móviles y de videojuegos, y análisis de macrodatos.|
|**S3 Intelligent-Tiering**|Este nivel es útil si sus datos contienen patrones de acceso desconocidos o cambiantes. S3 Intelligent-Tiering almacena los objetos en cuatro niveles: un nivel de acceso frecuente, un nivel de acceso poco frecuente, un nivel de acceso a instancias de archivo y un nivel de acceso al archivo. Amazon S3 supervisa los patrones de acceso de sus datos y los traslada de forma automática al nivel de almacenamiento más rentable en función de la frecuencia de acceso.|
|**S3 Standard - Acceso poco frecuente (S3 Standard-IA)**|Este nivel se utiliza para los datos a los que se accede con menor frecuencia, pero que requieren un acceso rápido cuando es necesario. S3 Standard-IA ofrece la alta durabilidad, el alto rendimiento y la baja latencia de S3 Standard, con precios económicos de almacenamiento y recuperación por GB. Este nivel de almacenamiento es ideal si desea almacenar copias de seguridad a largo plazo, archivos de recuperación de desastres, etc.|
|**S3 Express One Zone**|Optimizado para sus datos de acceso más frecuente y las aplicaciones de baja latencia dentro de una única zona de disponibilidad, a menudo se utiliza con los bucket de directorio de S3 para cargas de trabajo de alto rendimiento.|
|**S3 One Zone - Acceso poco frecuente (S3 One Zone-IA)**|A diferencia de otras clases de almacenamiento de S3 que almacenan los datos en un mínimo de tres zonas de disponibilidad, S3 One Zone - Acceso poco frecuente lo hace en una única zona de disponibilidad, lo que lo hace más económico que S3 Standard - Acceso poco frecuente. S3 One Zone - Acceso poco frecuente es ideal para los clientes que desean una opción de menor costo para los datos de acceso poco frecuente, pero que no necesitan la disponibilidad ni la resiliencia de S3 Standard o S3 Standard - Acceso poco frecuente. Es una buena opción para almacenar copias de seguridad secundarias de datos en las instalaciones o datos que se pueden volver a crear fácilmente.|
|**S3 Glacier Instant Retrieval**|Utilice S3 Glacier Instant Retrieval para archivar datos de acceso muy poco frecuente y que requieren una recuperación en milisegundos. Los datos que se almacenan en esta clase de almacenamiento implican un ahorro de costos de hasta un 68 % en comparación con la clase de almacenamiento S3 Standard-IA, con la misma latencia y rendimiento.|
|**S3 Glacier Flexible Retrieval**|S3 Glacier Flexible Retrieval brinda almacenamiento de bajo costo para los datos archivados a los que se accede una o dos veces al año. Con S3 Glacier Flexible Retrieval, se puede acceder a sus datos en tan solo 1 a 5 minutos mediante una recuperación acelerada. También puede solicitar recuperaciones masivas gratuitas en un máximo de 5 a 12 horas. Es una solución ideal para las copias de seguridad, la recuperación de desastres, las necesidades de almacenamiento de datos fuera de las instalaciones y para casos en los que algunos datos deben recuperarse en minutos.|
|**S3 Glacier Deep Archive**|S3 Glacier Deep Archive es la clase de almacenamiento de menor costo de Amazon S3. Admite la retención a largo plazo y la preservación digital de datos a los que se puede acceder una o dos veces al año. Los datos que se almacenan en la clase de almacenamiento S3 Glacier Deep Archive tienen un tiempo de recuperación predeterminado de 12 horas. Está diseñado para clientes que retienen conjuntos de datos por un periodo de 7 a 10 años o más, a fin de cumplir con los requisitos de conformidad normativa. Los ejemplos incluyen aquellos en industrias con alta regulación, como los servicios financieros, la sanidad y los sectores públicos.|
### Costo asociado

### Sub área

### Plataforma

| Nombre/Relación | Descripción de la relación           |
| --------------- | ------------------------------------ |
| [[!Aws]]        | Plataforma que provee el servicio    |
|                 | Plataforma que utiliza el servicio:w |

### Entidades asociadas
- [[!Servicios]]