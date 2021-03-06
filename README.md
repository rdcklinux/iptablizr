#iptablizr

iptables fácil para ti, es una utilidad completamente programada en bash, que ocupa comandos de sistema basicos
para entornos LINUX/UNIX Like, esto lo hace potente, rápido y liviano además fácil.

##comandos básicos
iniciar el servicio de iptables.
`scripts/start`


detiene el servicio de iptables.
`scripts/stop`

iniciar automáticamente el servicio.
`scripts/iptables-service start|stop|restart`

para que el servicio cargue automáticamente al iniciar el sistema
este debe ser cargado con:
`sudo update-rc.d iptables-service defaults`

comandos para permitir o bloquear un dominio o una ip
`command/addhost <alias> <tipo:domain|ip> <hostname|ip> <regla:deny|allow>`

comando para permitir o bloquear un puerto y su protocolo (prontamente estará disponible)
`command/addport <alias> [protocolo:tcp|udp] <port|ports> <regla:deny|allow>`

##configuración

###init.d/config

INET_IFACE=eth0
en este parametro debes especificar el nombre del adaptador con el cual se accede a internet, es decir,
la tarjeta de red que esta conectada a una EMTA un ROUTER o ADSL

INET_IP=192.168.0.29

en este parametro debes especificar la IP de adaptador de red que esta conectado a internet 

LAN_IFACE=eth1

en este parametro debes especificar el nombre del adaptador que va conectado al SWITCH/HUB o RED de computadores

LAN_IP=192.168.10.1

en este parametro debes especificar la IP de adaptador de red que va conectado a la RED

LAN_NET=192.168.10.0

en este parametro debes especificar la direccion de la red del adaptador que va conectado al SWITCH

LAN_MASK=24

en este parametro debes especificar la mascara de sub red que estas ocupando puedes usar notacion numerica o IP
Ej: 255.255.255.0 que es lo mismo que 24

###init.d/policy

iptables -P INPUT DROP

iptables -P FORWARD DROP

iptables -P OUTPUT ACCEPT

aca puedes especificar como debe comportarse el firewall en 
INPUT conexiones entrantes
FORWARD conexiones redirigidas
OUTPUT conexiones salientes

DROP denegar

ACCEPT permitir

en este caso todas las conexiones entrantes estan bloqueadas.
las redirecciones tambien pero las salidas permitidas, esta es la configuracion mas comun de un firewall.

###init.d/nat

aca puedes especificar las reglas de NAT
por defecto se espeficifica la regla de ENMASCARAMIENTO para que al redirigir la conexion no la deniege dado que es una 
ip que no esta en la subred del adaptador que tiene salida a internet.

###init.d/reset

este archivo define por defecto los parametros iniciales de iptables generalmente no es necesario modificarlo
a menos que se necesite hacer algo especial.

##Utilidades

`utils/getsubnet`

esta utilidad te permitira obtener las ip o subredes de un dominio.
esta utilidad es ocupada por los comandos que incluye esta herramienta.

##Estructura de Directorios

###rules.d/allow

####default
   
   comandos iptables por defecto para la regla permitir

otros archivos que se encuentren en este directorio son reglas para permitir servicios, dominios, etc..

###rules.d/deny

####default

   comando iptables por defecto para la regla denegar

otros archivos que se encuentren en este directorio son reglas para denegar servicio, dominios, etc...

##Extras

sugerencias o nuevas ideas son todas bienvenidas.

##ToDo
1. obtener INET_IP, LAN_IP, LAN_NET y LAN_MASK de forma automática
2. interfaz web sencilla para manipular los scripts y comandos
3. README.md in English
4. Improves to getsubnet
