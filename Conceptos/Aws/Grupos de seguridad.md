### Descripción
##### Notas grupos de seguridad
- Solo pueden contener reglas de "Allow".
- Pueden ser referenciados por grupos de seguridad o por ips
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
#### Inbound / Outbound rules
Inbound hace referencia a las reglas de entradas en los grupos de seguridad, las cuales permiten cierta conexión por equis puerto y protocolo. 
Outbound es la misma capacidad pero para la sálida desde el servicio asociado a dicho grupo de seguridad.
### Etiquetas
#AWS 
### Date