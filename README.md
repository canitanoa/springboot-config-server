# springboot-config-server
## Config Server MS	


> Cloud-config: 
- Es un servidor de configuración pensado para sistemas distribuidos. Su función es almacenar las propiedades de configuración de los microservicios del ecosistema.
- Nos sirve para Centralizar la configuración de todos los Microservicios en sistemas distribuidos, con diferentes ambientes (DESA, TEST, HOMO, PROD). 
- Y poder administrarla. La configuración por defecto se puede guardar en GIT o de forma física en un repo local.

> ¿Cómo funciona?
- Durante el arranque del microservicio, primero antes de registrarse en Eureka, va a consultar al servidor de configuración todos sus atributos, todas sus propiedades de 
configuración y una vez que las obtenga del repositorio Git, se va a registrar en Eureka y va a arrancar el servicio. Todo este proceso se realiza de forma transparente sin 
necesidad de una sola línea de código.
- Los ficheros de propiedades típicamente se nombrarán con el formato {microservice}-{profile}.{yml|properties} donde ‘microservice’ es el identificador de dicho microservicio 
y ‘profile’ un perfil de Spring.

> ¿Qué aporta?
- Cloud¬config se integra con Eureka de forma que durante el arranque de un microservicio, si éste es un Eureka client consultará al servidor Eureka donde se encuentra el 
servidor de configuración y le solicitará su configuración.
- Al almacenar la configuración en un repositorio git esto proporciona además de un repositorio centralizado de configuración, un histórico del mismo. Además cloud¬config 
añade funcionalidades a esta integración con git permitiendo consultar configuración de diferentes ramas.
- Permite gestionar configuración de diferentes entornos, etiquetarla y consultar por dichas etiquetas…
- Proporciona encriptado opcional para los valores de las propiedades.
- La existencia de ciertas anotaciones de Spring en integración con cloud¬config permiten recrear beans y reinicializar el contexto entero de Spring en caliente. 
Esto permite que los microservicios se adapten a cambios en las properties en caliente.

> ¿Como se configura?
- En el directorio del proyecto "springboot-config-server\src\main\resources\config":
  Se crean todos los archivos que configuran a los microservicios.
	- servicio-items.properties -> Se nombra com el mismo name del MS contiene la configuracion para ese servicio, 
	esto sobreescribe la configuracion que esta en el propio proyecto del MS cuando se utiliza este server.
	
	
