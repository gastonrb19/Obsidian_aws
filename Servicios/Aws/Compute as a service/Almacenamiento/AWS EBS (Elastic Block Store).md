### Descripción del servicio
Almacenamiento en bloque, divide los datos en bloques de tamaño fijo y es ideal para SO y bases de datos que requieren un acceso de baja latencia y actualizaciones frecuentes, ya que permite manipular de forma directa los bloques individuales

Como el nombre lo implica, Amazon Elastic Block Store (Amazon EBS) es un almacenamiento a nivel de bloques que usted puede conectar a una instancia de Amazon EC2. Puede comparar esto con todo lo que necesita para conectar una unidad externa a su portátil. Este almacenamiento conectable se denomina volumen de EBS. Estos volúmenes actúan de manera similar a las unidades externas en más de una forma.
- •
    **Desconectables:** puede desconectar un volumen de EBS de una instancia de EC2 y conectarlo a otra en la misma zona de disponibilidad para acceder a los datos que contiene.
- •
    **Independientes:** la unidad externa está separada del equipo. Esto significa que, si se produce un accidente y el equipo deja de funcionar, seguirá teniendo sus datos en la unidad externa. Lo mismo ocurre con los volúmenes de EBS.
- •
    **De tamaño limitado:** usted está limitado al tamaño de la unidad externa, ya que cuenta con un límite fijo en cuanto a su escalabilidad. Por ejemplo, es posible que tenga una unidad externa de 2 TB, lo que significa que solo puede disponer de 2 TB de contenido en ella. Esto también aplica a Amazon EBS, ya que un volumen también tiene un límite máximo en cuanto a la cantidad de contenido que puede almacenar en él.
- •
    **Conexión 1 a 1:** la mayoría de los volúmenes de EBS solo se pueden conectar con un equipo a la vez. La mayoría de los volúmenes de EBS tienen una relación de uno a uno con las instancias de EC2, por lo que no pueden compartirse ni conectarse a varias instancias a la vez.
> [!New]
> **AWS anunció la característica de conexión múltiple de Amazon EBS que permite conectar volúmenes SSD (io1 o io2) de IOPS aprovisionadas a varias instancias de EC2 a la vez. Esta característica no está disponible para todos los tipos de instancias; además, todas las instancias deben estar en la misma zona de disponibilidad.**
#### Tipo de volúmenes de EBS
Los volúmenes de EBS se organizan en dos categorías principales:
- **HDD**: Se utilizan para grandes cargas de trabajo de streaming que necesitan un alto rendimiento. 
	- ![[Captura de pantalla 2026-09-10 a las 10.25.37 p. m..png]]
- **SSD**: Se utilizan para operaciones frecuentes de lectura/escritura con un tamaño de E/S pequeño.
	-  ![[Captura de pantalla 2026-09-10 a las 10.23.33 p. m..png]]
#### Beneficios EBS
- Alta disponibilidad
	Cuando crea un volumen de EBS, este se replica automáticamente en su zona de disponibilidad para evitar la pérdida de datos en puntos de error únicos.
- Persistencia de datos
	El almacenamiento persiste incluso cuando la instancia no lo hace.
- Cifrado de datos
	Cuando el usuario los activa, todos los volúmenes de EBS admiten el cifrado.
- Flexibilidad
	Los volúmenes de EBS admiten cambios sobre la marcha. Modifique el tipo y tamaño del volumen y la capacidad de operaciones de entrada/salida por segundo (IOPS) sin detener la instancia.
- Copias de seguridad
	Amazon EBS permite crear copias de seguridad de cualquier volumen de EBS.
#### Instantáneas de Amazon EBS
Los errores ocurren. Un error es no hacer copias de seguridad de los datos y perderlos de forma inevitable. Para que esto no suceda, siempre haga una copia de seguridad de sus datos, incluso en AWS. Dado que los volúmenes de EBS se componen de los datos de su instancia de EC2, debe realizar copias de seguridad de estos volúmenes, lo que se conoce como instantáneas.
Estas instantáneas de EBS son copias de seguridad progresivas que solo guardan los bloques del volumen que se modificaron después de la última instantánea. Por ejemplo, si en un volumen tiene 10 GB de datos y solo se modificaron 2 GB de datos desde la última instantánea, solo los 2 GB modificados se escriben en Amazon S3

### Costo asociado

### Sub área

### Entidades asociadas
- [[!Almacenamiento]]
### Etiquetas
#AWS
