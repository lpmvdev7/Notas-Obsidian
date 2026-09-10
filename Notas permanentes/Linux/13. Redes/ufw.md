Tipo: Nota permanente
Fecha: 2026-08-10
Referencias:
* tldr 
Temas: #Redes #Linux #Comandos 
### ¿Que hace el comando?
ufw (uncomplicated firewall) es un comando que nos permite manipular el firewall en linux.

### Uso del comando
A continuación estaremos mostrando algunas formas que tenemos de usar el comando ufw para manipular el firewall.
```bash
# Habilitrar el firewall
sudo ufw enable

# deshabilitar el firewall
sudo ufw disable

# Permtir la entrada de cualquier sitio al puerto 53
sudo ufw allow 53

# Permite la entrada de cualquier sitio al puerto 25
sudo ufw allow 25/tcp

# Denegar el acceso a un puerto
sudo ufw deny 53

# Permitir el trafico http entrante a nuestro computador
sudo ufw allow in http

# Permitir el trafico saliente de http 
sudo ufw allow out http

# Bloquear el trafico saliente hacia https
sudo ufw deny out 443/https

# Bloquer el trafico saliente hacia https colocando un comentario para identificar la regla
sudo ufw deny out 80 comment "Denegar trafico saliente puerto 80"

# Mostrar el estado general del firewall
sudo ufw status

```

La mayoría de los usos que coloco aquí, no cubren ni la mitad de las cosas que se pueden llegar a crear con ufw utilizando el comando e incluso combinándolo con bash scripting. Le recomiendo al pablo del futuro o a quien sea que se encuentre leyendo esto checar ufw mediante comandos como man, tldr o con la opción --help.

```bash
# Abrir el manual de ufw
man ufw

# Ejemplos de como ussr el comando ufw
tldr ufw

# Todos los comandos que puedes usar con ufw
ufw --help
```

### Caso de uso del comando UFW

#### Ejemplo 1
Tenemos un servidor linux, que acaba de ponerse en producción, en el tenemos lo siguiente:
* Un servidor web escuchando en el puerto 80
* HTTPS en el puerto 443
* SSH en el puerto 22 para administración
* No quieres que otros servicios puedan recibir conexiones desde Internet
El administrador nos pide que ssh solamente pueda ser accesible desde la red interna 192.168.1.0/24. HTTP y HTTPS deben seguir siendo accesibles desde Internet.
```bash
sudo ufw allow from 192.168.1.0 to any port 22 proto tcp 
```

#### Ejemplo 2
Tenemos una maquina linux que funciona como servidor de desarrollo, actualmente contamos con los siguientes servicios.
* SSH -> 22
* HTTP -> 80
* HTTPS -> 443
* Node.js -> 3000
* PostgreSQL -> 5432

Actualmente UFW esta activo y permite la entrada de trafico de cualquier lado hacia cualquiera de los puertos anteriormente mencionados.

¿Que tenemos que hacer?
1. SSH solo puede poder utilizar la red administrativa 192.168.1.0/24
2. HTTP y HTTPS deben permanecer accesibles desde cualquier lugar.
3. Node.js solo debe ser accesible desde la red local: 192.168.1.0/24
4. PostgreSQL debe quedar completamente bloqueado desde conexiones externas, el servidor solamente necesita que PostgreSQL se utilizado locamente
5. El trafico saliente debe permanecer permitido

```bash

# Permitir el acceso de una ip a cualquiera para el puerto 22 
sudo ufw allow from 192.168.1.0/24 to any port 22 proto tcp

# Permitir al trafico entrante acceder mediante el puerto 80
sudo ufw allow 80/tcp

# Permitir al trafico entrante acceder mediante el puerto 443
sudo ufw allow 443/tcp

# Permitir el acceso al puerto 3000 a partir de una ip dada
sudo ufw allow from 192.168.1.0/24 to any port 3000 proto tcp

# Denegar el trafico entrante al puerto 5432
sudo ufw deny in 5432/tcp

```
### Notas Relacionadas
[[comandos-linux]]
[[iptables]]
[[nftables]]
[[Firewall]]

