Tipo: Nota permanente
Fecha: 2026-08-04
Referencias:
* Linux.pdf
Temas: #daemons 
### ¿Que es systemd?
systemd es el sistema de inicio y administrador de servicios en linux, es ampliamente utilizado en la mayoría de las distribuciones modernas de Linux. Como administrador de servicios en Linux, systemd es el proceso padre de todo el sistema, siendo el responsable de iniciar, detener y supervisar los servicios y otros recursos del sistema.
La capacidad de administración de systemd sobre los servicios en linux se remonta a su capacidad para leer las instrucciones escritas en archivos conocidos como unit-files, estos archivos pueden representar:
* .service: servicios del sistema
* .timer: tareas programadas
* .socket: sockets
* .mount: puntos de montaje
Por lo general estos tipos de archivos se encuentran en esta ubicación:
```
cd /etc/systemd/system/
```

Archivos como estos son la razón por la cual podemos administrar servidores web, bases de datos, servidores de archivos y muchas otras cosas.  Esto convierte a systemd en uno de los pilares fundamentales de linux.

![](https://www.muylinux.com/wp-content/uploads/2022/05/systemd.png)
### Notas Relacionadas
[[Servicios linux]]
[[pstree]]
[[About - Procesos en linux]]
[[systemctl]]
