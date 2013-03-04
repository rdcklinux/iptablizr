iptablizr
=========

iptables made easy for you

Spanish/English Documentation

iptables fácil para ti, es una utilidad completamente programada en bash, que ocupa comandos de sistema basicos
para entornos LINUX/UNIX Like, esto lo hace potente, rapido y liviano ademas de fácil.

comandos basicos

scripts/start
inicia el servicio de iptables

scripts/stop
detiene el servicio de iptables

scripts/iptables-service
para que el servicio cargue automaticamente al iniciar el sistema
este debe ser cargado con:
sudo update-rc.d iptables-service defaults

comandos para permitir o bloquear
command/insert <name> <domain|ip> <hostname> <deny|allow>
