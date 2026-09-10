Tipo: Nota permanente
Fecha: 2026-08-12
Referencias:
* Linux.pdf
Temas: 
### ¿Para que sirve?
El reenvió de puertos en SSH sirve para acceder de forma segura a servicios de una red remota que nos están directamente expuestos a la computadora. De esta manera hacemos que el trafico viaje a través de un tunel SSH.

El reenvió se puede hacer de dos formas, locales y remotas.

### Reenvió de puertos locales
El reenvio de puertos locales permite reenviar un puerto desde nuestro computadora a un puerto ubicado en un servidor remoto. 
```bash
ssh -L <puerto_local>:<host_destino>:<puerto_destino> <usuario>@<servidor_ssh>
# <puerto_local> puerto de nuestro computador
# <host_destino> host al que se reenviara la conexion
# <puerto destino> puerto del servicio destino
# <usuario> usuario del servidor ssh
# <servidor_ssh> servidor mediante el cual se crea el tunel
```

En este ejemplo lo que estoy haciendo es lo siguiente:
>Quiero que en el puerto 3000 de mi computador me muestres todo lo que se encuentra en localhost:8080 del servidor remoto, de esa manera yo desde mi maquina local podre ver lo que ese servidor esta mostrando en ese puerto.
```bash
ssh -L 3000:localhost:8080 deploy@10.20.2.0
```

Con el reenvio de puertos locales podemos acceder desde nuestra computadora a servicios que se ejecutan en servidores remotos, como aplicaciones en desarrollo, dashboards o bases de datos, sin necesidad de exponer directamente esos servicios a nuestra red.

### Reenvío de puertos remotos.
El reenvio de puertos remotos consiste en tomar un puerto local des nuestro computador y pasar su contenido a través de un tunel ssh hacia un puerto remoto, de esta forma podemos hacer accesible desde un servidor remoto un servicio que corre locamente en nuestra maquina.
```bash
ssh -R puerto_remoto:host_destino:puerto_local usuario@servidor_remoto
```

En este ejemplo lo que estoy haciendo es lo siguiente:
>Quiero que en el puerto 3000 del servidor cuya ip es 192.168.1.100 expongas lo que tengo ejecutando en el puerto 8080 de mi computador
```bash
ssh -R 3000:localhost:8080 pablo@192.168.1.100
```

>DETALLE IMPORTANTE: 
>Cuando hacemos reenvió de puertos con la opcion -R, por defecto SSH únicamente permite que el propio servidor, cuyo puerto expusimos, tenga acceso al servicio. Es decir, que la computadora desde la cual ejecutamos el comando y otras computadoras dentro de la misma red no pueden acceder al servicio. Si queremos que puedan acceder, tendremos que habilitar la opción **GatewayPorts yes** en el archivo **/etc/ssh/sshd_config** del servidor y reiniciar el servicio SSH.


### Ejercicios 

>**Escenario 1 - Reenvio de puertos locales**
>Trabajas en tu laptop. En la empresa hay un servidor de base de datos **(db-servidor - 10.0.0.50)** el cual solo es accesible dentro de la red interna corporativa, este servidor se encuentra corriendo PostgreSQL en el puerto 5432. Estas en la oficina, pero tienes acceso SSH a un servidor bastion que si esta dentro de esa red.
>Tu objetivo es acceder al servidor de base de datos desde la laptop, como si estuviera en tu localhost.

```bash
ssh -L 5432:10.0.0.50:5432 pablo@bastion.miempresa.com
```

>**Escenario 2 - Reenvio de puertos remotos**
>Estas desarrollando una app web en tu laptop, corriendo en **localhost:3000**. Un cliente quiere ver una demo en vivo, pero tu laptop no tiene IP publica. Tienes acceso SSH a un servidor con IP publica **demo.miservidor.com**
>Tu objetivo es exponer tu app local para que el cliente la vea desde Internet, a través del servidor con IP publica.

```bash
ssh -R 3000:localhost:3000 pablo@demo.miservidor.com
```


### Notas Relacionadas
[[comandos-linux]]
[[secure shell]]
[[ssh]]
[[ssh-keygen]]
[[ssh-keyscan]]
[[ssh-copy-id]]


