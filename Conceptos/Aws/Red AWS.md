	### Descripción
> **Importante**: Las redes se pueden crear a nivel regional y estas pueden utilizar diferentes zonas de disponibilidad que estén dentro de esta misma región. 
#### IPV4
Composición de un octateto de 8 bits cada una de sus posiciones las cuales determinan la dirección asociada.
> 192.191.190.1/8
#### IPV6
Composición de un Hexagecimal. 
Composición del bloque (Ejemplo: `2001:0db8:85a3:0000:0000:8a2e:0370:7334/64`)
- **Tamaño por grupo:** Cada grupo (hexteto) equivale a **16 bits** (‭$8 \times 16 = \mathbf{128\text{ bits en total}}$)
- **Valores posibles:** Del `0` al `9` y de la `a` a la `f` (hexadecimal).
#### CIDR
Composición del **CIDR** (Ejemplo por analogía: `192.168.190.1/8`)  

- **192:** País (1.ᵉʳ octeto = 8 bits)  
    
- **168:** Ciudad (2.º octeto = 8 bits)  
    
- **190:** Zona (3.ᵉʳ octeto = 8 bits)  
    
- **1:** Dirección / Host (4.º octeto = 8 bits)  
    
- **/8:** Prefijo o máscara de red que indica la cantidad de bits fijos (de un total de 32) para identificar la red.  
    ⚬ **A mayor número (hasta** **`/32`****):** Más bits bloqueados para la red.
    Menos IPs/equipos disponibles** (red más pequeña).  
    **A menor número (hacia** **`/0`****):** Menos bits bloqueados ‭
    **Más IPs/equipos disponibles** (red más grande).
#### Aws composición de red
**Intervalos de CIDR admitidos por AWS**

De los 32 bits en una dirección IPv4, AWS permite utilizar hasta 28 bits para identificar una red, los 4 bits restantes en la dirección IP de 32 bits pueden utilizarse para identificar los recursos en una subred. Esto, a su vez, permite agregar hasta 16 recursos en la subred.

Debe usar al menos 16 bits para identificar una red, mientras que los 16 bits restantes se pueden usar para identificar los recursos de la subred, lo que permite hasta 65 536 recursos en la subred.

En resumen, la red se puede identificar usando de 16 a 28 bits en la dirección IPv4 de 32 bits. Por otro lado, los recursos en la subred se pueden identificar con 4 a 16 bits en la dirección IPv4 de 32 bits.
#### Subredes (Subnets)  
- **Segmentación:** A partir del bloque CIDR principal de la VPC (ej. `/16`), se pueden crear subredes más pequeñas aumentando el prefijo (ej. `/24`) para organizar y aislar recursos.  
- **Ubicación:** **Cada subred pertenece exclusivamente a una única Zona de Disponibilidad (AZ)** dentro de la región.  
#### Puerta de Enlace a Internet (Internet Gateway - IGW)  
- Componente administrado de VPC que permite la comunicación bidireccional entre los recursos de la VPC e Internet.  
- Realiza la traducción de direcciones (NAT 1:1) entre IPs privadas y públicas.  
- **Nota clave:** El IGW **no filtra puertos ni protocolos**; solo enruta tráfico. El filtrado de puertos se delega a las _NACLs_ (a nivel subred) y _Security Groups_ (a nivel recurso).  
#### Subred Pública vs. Subred Privada  
- **Subred Pública:** Su **Tabla de Rutas (Route Table)** contiene una regla explícita que envía el tráfico a Internet (`0.0.0.0/0`) hacia el **Internet Gateway (****`igw-xxxx`****)**, y sus recursos tienen IPs públicas asignadas.  
    
- **Subred Privada:** Su tabla de rutas **no apunta al IGW** (solo tiene la ruta `local`). Los recursos no son accesibles directamente desde Internet.  
#### Ejemplo de Arquitectura Común  
- **Subred Pública (DMZ/Frontend/ALB):** Aloja balanceadores de carga o servidores web con acceso directo desde Internet a través del IGW.  
- **Subred Privada (Backend/Base de Datos):** Aloja APIs internas y bases de datos aisladas. Si estas máquinas requieren descargar parches o actualizar paquetes desde Internet sin quedar expuestas, el tráfico de salida se envía a través de un **NAT Gateway** ubicado en la subred pública.
### Firewall
- Un firewall sin estado permite que todo el tráfico pueda "pasar". 
- Un firewall con estado realiza la restricción, ya que tiene reglas en su estado listas para restringir. 

### Reglas ACL
Una ACL de la red es una capa opcional de seguridad para su VPC que actúa como un firewall a fin de controlar el tráfico dentro y fuera de una o más subredes. Cada VPC viene automáticamente con una ACL de la red predeterminada. Permite todo el tráfico de IPv4 entrante y saliente.

Las ACL de la red **no tienen estado**, lo que significa que las respuestas al tráfico entrante permitido están sujetas a las reglas para el tráfico saliente (y viceversa).

![[Captura de pantalla 2026-09-06 a las 10.31.27 p. m..png]]

### Grupos de seguridad
Los grupos de seguridad funcionan como un firewall virtual de la instancia para controlar el tráfico entrante y saliente. Los grupos de seguridad actúan en el nivel de la interfaz de red, no en el nivel de la subred, y solo admiten reglas de **permiso**.

Un grupo de seguridad permite el tráfico en función de un protocolo IP, un puerto o una dirección IP, y utiliza reglas con estado. El tráfico se puede restringir con cualquier protocolo IP, puerto de servicio y dirección IP de origen o destino (dirección IP individual o bloque de CIDR).
![[Captura de pantalla 2026-09-06 a las 10.34.43 p. m..png]]

#### Cadena de grupos que permite la mayor seguridad entre servicios.
![[Captura de pantalla 2026-09-06 a las 10.39.27 p. m..png]]

#### **Comparación entre grupos de seguridad y ACL de la red**

Un grupo de seguridad funciona como firewalls para las instancias de EC2 asociadas, ya que controla el tráfico entrante y saliente en el nivel de la instancia. Las ACL de la red actúan como un firewall para las subredes asociadas y controlan el tráfico entrante y saliente en el nivel de la subred. Una ACL de la red deniega la comunicación de forma predeterminada. El orden de las reglas de la ACL de la red es importante.

| **Grupo de seguridad**                                                                                                                                            | **ACL de la red**                                                      |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Los grupos de seguridad actúan como un firewall para instancias de EC2 asociadas y están asociados con la interfaz de red elástica implementada por un hipervisor | Las ACL de la red actúan como un firewall para las subredes asociadas  |
| Controlan el tráfico entrante y saliente al nivel de la instancia                                                                                                 | Controlan el tráfico entrante y saliente al nivel de la subred         |
| Solo admite reglas de permiso                                                                                                                                     | Admite las reglas de permiso y denegación                              |
| Es un firewall con estado                                                                                                                                         | Es un firewall sin estado                                              |
| Se debe asignar manualmente a las instancias                                                                                                                      | Se aplica automáticamente cuando las instancias se agregan a la subred |
### Etiquetas
#AWS #Cloud #Network
### Date

### Relaciones
- [[!Conceptos]]
