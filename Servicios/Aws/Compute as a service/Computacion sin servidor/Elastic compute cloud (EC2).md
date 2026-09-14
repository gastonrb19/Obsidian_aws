### Descripción del servicio
Servicio de aprovisionamiento que permite ejecutar maquinas virtuales en AWS.

#### Consideraciones para una instancia EC2
- **Nombre y etiquetas**
	- En aws es posible asignar una "etiqueta", esta asigna metadatos a nuestros recursos. Los cuales pueden ayudarnos a organizar nuestros servicios aprovisionados.
- **Aplicaciones e imagen de SO**
	- ¿Qué aplicación y sistema operativo ejecutara en esta instancia?
- **Tipo y tamaño de la instancia**
	- ¿Qué requisitos técnicos debe cumplir?
- **Par de claves**
	- Como conectará la instancia con otros componentes de la app y como autenticará el acceso a la instancia
- **Redes y seguridad**
	- Que VPC utilizará
- **Configuración del almacenamiento**
	- Que tipo de almacenamiento es mejor para su caso 
- **Ubicación y tenencia**
	- Donde ejecutará sus instancias EC2
- **Scripts y metadatos**
	- Que puede hacer para automatizar el lanzamiento de la instancia
#### Imagen de máquina de Amazon (AMI)
En cortas palabras las AMI es semejante a una imagen ISO, lo cual contiene información del sistema operativo y también para amazon de la configuración para el aprovisionamiento de esta.
Podemos encontrar AMI en el marketplace de AWS, prediseñadas y también utilizar propias que estén diseñadas. Además, también podemos realizar nuestras AMI a través del aprovisionamiento de una instancia y guardar la configuración realizada para esta.

Una AMI incluye lo siguiente:
- •
    Una plantilla para el volumen raíz de la instancia (por ejemplo, un sistema operativo, aplicaciones y un servidor de aplicaciones).
- •
    Permisos de lanzamiento que controlan qué cuentas de AWS pueden utilizar la AMI para lanzar instancias.
- •
    Asignación de dispositivos de bloques que especifica los volúmenes que deben adjuntarse a la instancia cuando se lanza.
#### Explicación de los nombres de tipos de instancias
Puede elegir entre más de 400 tipos de instancias de EC2 para poner en marcha las aplicaciones que traslade a la nube. Cada tipo de instancia viene en diferentes tamaños, con diferentes asignaciones de CPU virtuales (vCPU) y memoria. Elegir los tamaños de instancia correctos es fundamental para usarlos de manera eficiente. El tipo completo de una instancia consta del nombre de la familia seguido del número de generación, cualquier propiedad adicional y el tamaño.
#### Información composición nombre de una instancia
##### Familias de instancias
![[Captura de pantalla 2026-09-08 a las 10.59.15 p. m..png]]
**Uso por tipo de instancia**
- Uso general:
	-  Equilibrio entre computación, memoria y redes
	- Cargas de trabajo diversas
	- Aplicaciones web
- Optimizadas para la computación:
	- Aplicaciones vinculadas a cómputo
	- Procesadores de alto rendimiento
	- Transcodificación de medios
	- Modelado científico
	- Machine learning
- Optimizadas para memoria:
	- Entrega rápida de conjuntos de datos grandes en la memoria
	- Servidores de base de datos
	- Cachés web
	- Análisis de datos
- Computo acelerado:
	-  Procesamiento de gráficos elevado
	- Enlazado a GPU
	- Machine learning
	- Cómputo de alto rendimiento (HPC)
	- Vehículos autónomos
- Optimizadas para almacenamiento:
	- Lectura/escritura secuencial elevadas
	- Conjuntos de datos grandes
	- Bases de datos NoSQL
	- Amazon OpenSearch Service
- Optimizadas para el computo de alto rendimiento:
	- Personalizadas 
	- Cargas de trabajo de computación de alto rendimiento (HPC) con uso intensivo de computación
	- Cargas de trabajo a escala
#### Pares de claves
Un par de claves, que consta de una clave privada y una clave pública, es un conjunto de credenciales de seguridad que utiliza para probar su identidad cuando se conecta a una instancia. Amazon EC2 almacena la clave pública y usted almacena la clave privada. Utiliza la clave privada en lugar de una contraseña para acceder de forma segura a sus instancias. Cualquier persona que posea sus claves privadas puede conectarse a sus instancias, por lo que es importante que almacene dichas claves privadas en un lugar seguro.

#### Tenencia
La tenencia de computación de AWS es la forma en que las instancias de EC2 se distribuyen en el hardware físico subyacente, con tres opciones principales: tenencia compartida, instancia dedicada o host dedicado. La elección de la tenencia depende de sus requisitos específicos en torno al cumplimiento, las licencias y la optimización de costos.
- Tenencia compartida:
	- De forma predeterminada, las instancias de EC2 tienen tenencia compartida, lo que significa que varias cuentas de AWS pueden compartir el mismo hardware físico.
- Instancia dedicada:
	- Las instancias dedicadas son instancias de EC2 que, a nivel de hardware del host, están aisladas físicamente de las instancias no dedicadas y de las instancias que pertenecen a otras cuentas de AWS.
- Host dedicado:
	- Cuando lanza instancias en un servidor dedicado, las instancias se ejecutan en un servidor físico con capacidad de instancias de EC2 totalmente dedicado a su uso. Se le proporciona un servidor aislado con configuraciones que puede controlar. 

Con los hosts dedicados, tiene la opción de permitir que AWS seleccione automáticamente un servidor para colocar su instancia. O puede seleccionar manualmente un servidor dedicado para colocar su instancia.

#### Grupos de ubicación y sus casos de uso
El servicio de Amazon EC2 intenta distribuir todas sus instancias en el hardware subyacente para minimizar los errores correlacionados. Puede usar grupos de ubicación para influir en la ubicación de un grupo de instancias interdependientes con el fin de satisfacer las necesidades de la carga de trabajo.
- •
    Los **grupos con ubicación en clúster** se recomiendan para las aplicaciones que se beneficien de una baja latencia de red, un elevado rendimiento de red o ambas cosas. También son recomendables cuando la mayor parte del tráfico de red se da entre las instancias del grupo. Las cargas de trabajo de HPC pueden requerir este nivel de conectividad en su VPC.
- •
    Se recomienda usar **grupos de ubicación distribuida** en aplicaciones con pocas instancias críticas que deben mantenerse separadas entre sí. Los servicios que requieren el máximo tiempo de actividad, como un sistema de registro médico de salud, son más tolerantes a errores en una distribución.
- •
    Los **grupos de ubicación de particiones** se pueden utilizar para implementar grandes cargas de trabajo distribuidas y replicadas. Evite errores de hardware al mismo tiempo para múltiples componentes mediante el uso de particiones. ### Costo asociado
#### Datos de usuario
Al realizar el lanzamiento de una instancia se puede ejecutar un script en este lanzamiento, con el fin de automatizar cierto proceso.
![[Captura de pantalla 2026-09-08 a las 11.12.57 p. m..png]]
### Sub área

### Servicios que utilizan este servicio

| Nombre                                       | Descripción de la relación                                                                                                                                                                                                                                                                                                                                                          |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Amazon relational database service (RDS)]] | Debajo de la instancia de base de datos hay una instancia de EC2. Sin embargo, esta instancia se administra a través de la consola de Amazon RDS en lugar de la consola de Amazon EC2. Al crear la instancia de base de datos, elige el tipo y el tamaño de la instancia. La clase de instancia de base de datos que elija influye en la capacidad de procesamiento y la memoria de |
|                                              |                                                                                                                                                                                                                                                                                                                                                                                     |
|                                              |                                                                                                                                                                                                                                                                                                                                                                                     |

### Entidades asociadas
- [[!Computacion sin servidor]]
- [[Computación como servicio (compute as a service)]]
### Etiquetas
#AWS
