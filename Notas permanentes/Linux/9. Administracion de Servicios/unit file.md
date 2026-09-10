Tipo: Nota permanente
Fecha: 2026-08-04
Referencias:
* Linux.pdf
* https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/using_systemd_unit_files_to_customize_and_optimize_your_system/assembly_working-with-systemd-unit-files_working-with-systemd#tabl-systemd-Unit_Sec_Options
Temas: #daemons 
### ¿Que son los unit file?
Los unit file son aquellos archivos de los que nace un servicio o daemon en linux, por lo general estos archivos tienen una extensión .service, aunque esta no es la única.
Dentro de estos archivos viven instrucciones que ayudan a systemd en la administración de recursos del sistema.
Existen varios tipo de unit files pero a mi me gustaría hablar de dos:
* .service: Unit file que representa un servicio como nginx, apache, docker, ssh o uno que nosotros hemos creado.
* .timer: Unit file que sirve para ejecutar tareas a horas especificas, vendría siendo una alternativa a cron.

### Partes de un unit file
Los archivos UNIT se dividen en tres partes:
1. Unit: Describe información general del servicio
2. Service: Definimos el comportamiento del servicio
3. Install: Definimos como y cuando se habilita el servicio.

### Ejemplo de un unit file
Creamos un pequeño script en la carpeta **/usr/local/bin**
```bash
#! /bin/bash
echo "El usuario $(whoami) encendio la latptop en la siguiente fecha: $(date +'%m-%d-%Y')" >> /home/pablo/fechaInfoService.txt

```

Nos dirigimos a la siguiente carpeta
```bash
cd /etc/systemd/system
```

Una vez allí creamos el siguiente archivo
```bash
sudo vim fechaInfoService.service
```

Dentro de nuestro unit file colocamos lo siguiente:
```bash
[Unit]
Description="Imprimir hora en la que root esta utilizando la computadora"

[Service]
ExecStart=/usr/local/bin/fechaInfoService.sh

[Install]
WantedBy=multi-user.target
```

Recargamos los servicios para que el servicio que acabamos de crear aparezca
```bash
sudo systemctl daemon-reload
```

Vemos el status de nuestro servicio
```bash
sudo systemctl status fechaInfoService
○ fechaInfoService.service - "Imprimir hora en la que un usuario esta utilizando la computadora"
     Loaded: loaded (/etc/systemd/system/fechaInfoService.service; disabled; preset: enabled)
     Active: inactive (dead)

```

Iniciamos el servicio
```bash
sudo systemctl start fechaInfoService
```

Ahora, como queremos que este servicio siempre inicie junto con systemd ejecutamos el siguiente comando:
```bash
sudo systemctl enable fechaInfoService
```

En /home/pablo veremos que el archivo fechaInfoService.txt ya contiene la ejecución de nuestro servicio.
```bash
cat fechaInfoService.txt 
El usuario root encendio la latptop en la siguiente fecha: 08-04-2026
```
### Notas Relacionadas
[[systemd]]
[[Bash Scripting]]
[[Administracion con systemctl]]
[[systemctl]]
