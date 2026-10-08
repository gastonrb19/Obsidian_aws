### Descripción del servicio
This is a logical component in a VPC that represents a virtual network card.
- The ENI can have the following attributes:
	- Primary private ipv4, one or more secondary IPV4
	- One elastic IPV4, one or more secondary IPV4
	- One public IPV4
	- One or more security groups
	- A MAC address
- You can create ENI independently and attach them on the fly (move them) on EC2 instances for failover
- Bound to a specific availability zone (AZ)
With this we can create an IPV4 and have more control on them. This private instances won't delete with the instances. In cases of delete an instance or something shut down we can pass the ENI to a new instance (attach to that instance).F

**Is associated with a AZ**
### Costo asociado

### Sub área

### Servicios que utilizan este servicio

| Servicio                         | Descripción de la relación                                                                                |
| -------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [[Elastic compute cloud (EC2)]]] | This subservice is useful as a logical component to connect in a VPC, which already is the EC2 instance.  |

### Entidades asociadas
- [[!Network]]
### Etiquetas
