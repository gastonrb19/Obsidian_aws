### Descripción del servicio
Servicio asociado a la gestión de permisos y accesos para los diferentes servicios presentes.
Por defecto este servicio crea la cuenta Root, la cual no debería ser utilizada ni compartida.

#### Usuarios
Los usuarios son las diferentes cuentas asociadas a un acceso con diferentes privilegios y permisos en AWS.
#### Grupos
Un grupo permite realizar la agrupación de los usuarios y establecer directrices para este conjunto de usuarios. 
Un usuario puede estar en diferentes grupos, pero un grupo no puede contener otro grupo. 
#### Policies
JSON con la información referentes a los permisos que tiene asociado, ya sea un usuario o un grupo.
Estas pueden ser creadas directamente por un grupo, por un usuario. Además podemos verlas a través de su formato JSON, como del formato visual en la console con el servicio IAM.
#### Password Policy
Mediante las politicas de contraseña podemos definir:
- largo de una contraseña
- lowercasse letters
- numbers
- non-alphanumeric characters
- Permitir que los IAM user generen cambios en su contraseña
- Que la contraseña expire y deban realizar cambio de esta.
- Prevenir reutilizar una contraseña.
#### MFA (Multi factor authentication)
Esta es una posibilidad para aumentar la seguridad en las cuentas mediante una app de autenticación de dos pasos.
##### Policies structure
```
{
	Version: "2012-10-17", // Policy language version
	"Id": "S3-Account-Permissions", // identifier for the policy (opt)
	"Statement" : [ // One or more individual statements (req)
	{
		"Sid": "1",//identifier for the statement (opt)
		"Effect": "Allow",//(allow or deny)
		"Principal": {//Which account/role applied to
			"AWS": ["arn:aws:iam::123456789012:root"]
		},
		"Action": [//List of actions this policy allows or denies
			"s3:GetObject",
			"s3:PutObject",
		],
		"Resource": ["arn:aws:s3::mybucket/*"]//List of resources to which the actions applied to.
	}
	]
} // There is the possibility to have conditions when it is necessary
```
#### Roles
Permite dar privilegios a los usuarios mediante politicas (policies) y después asignarlas, estás pueden ser de manera individual por cada servicio o diferentes servicios.
#### IAM Credential Report (account-level)
Reporte que lista todas las cuentas de los diferentes usuario, su estatus de credenciales.
#### IAM access advisor (user-level)
Reporte que te informa del uso de los permisos, con el fin de gestionar los roles/politicas correctas para cada usuario.
### Costo asociado

### Sub área

### Servicios que utilizan este servicio

| Servicio | Descripción de la relación |
| -------- | -------------------------- |
|          |                            |

### Entidades asociadas
- [[!Gestión y permisos]]
### Etiquetas
#AWS #Global

