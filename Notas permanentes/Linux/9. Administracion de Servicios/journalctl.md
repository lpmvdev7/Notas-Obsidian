Tipo: Nota permanente
Fecha: 2026-08-04
Referencias:
* Linux.pdf
Temas: #daemons #logs 
### ¿Que hace el comando?
Este comando nos permite manipular los logs proporcionados por journald, esto quiere decir que es una herramientas que nos ayuda en la traza de errores en nuestro sistema.

### Como usar el comando
El comando journalctl nos sirve para mostrarnos los logs del sistema desde el mas viejo al mas nuevo.
```bash
journalctl
```

También podemos ver los logs del mas reciente al mas viejo
```bash
journalctl -r
```

Como pudimos ver, al ejecutar los comandos anteriores nuestra pantalla se llena de logs, en estos casos journalctl nos permite mostrar solo cierto numero de logs.
```bash
journalctl -n 10
```

Ver los logs en tiempo real
```bash
journalctl -f
```

Con journalctl también podemos listar el id de las ultimas sesiones y en base a ese id (IDX), empezar a buscar errores en el servidor.
```bash
journalctl --list-boots 
IDX BOOT ID                          FIRST ENTRY                 LAST ENTRY                 
-24 889a76a0cf6145eb910295f05dacc202 Tue 2026-07-21 09:28:29 CST Tue 2026-07-21 17:49:27 CST
-23 05c512388bd741438b89ca7df0d0a25a Tue 2026-07-21 17:52:45 CST Wed 2026-07-22 00:57:43 CST
```

Ver los logs de una sesión especifica
```bash
journalctl -b -24
```

El comando journalctl también nos permite ver los logs en especifico de un servicio
```bash
journalctl -u docker.service 
```

Podemos filtrar los logs del sistema partiendo desde un periodo de tiempo específico utilizando términos como ayer, hoy o mañana, hora y fechas.
```bash
journalctl --since=yesterday --until=today
```

Haciendo uso de comandos como ps o htop podemos encontrar el id de un proceso en especifico y ver todos sus logs relacionados.
```bash
#Aqui estoy viendo todos los logs de google chrome
journalctl _PID=3051
```

También podemos ver los logs de un usuario en especifico
```bash
#Logs del usuario ollama
journalctl _UID=997
```

Si queremos que los logs que se nos muestran sean un poco mas descriptivos podemos usar el siguiente comando:
```bash
journalctl -xe
```

### Caso de uso
Tenemos el rol de administrador en un servidor Linux donde se encuentra alojada una aplicacion web. Esta mañana, uno de nuestros compañeros nos informa que la aplicación ya no esta disponible.
El servidor fue reiniciado durante la noche para aplicar unas actualizaciones, por lo que sospechamos que el problema comenzó después del reinicio.
Nuestra tarea como administradores consiste en investigar los registros del sistema para responder las siguientes preguntas:
* ¿En que arranque ocurrió el problema?
* ¿Que mensajes de error aparecieron después del reinicio?
* ¿El servicio de la aplicación nginx, docker, genero algún error?
* ¿A que hora comenzaron a aparecer los errores?
* ¿Que información adicional proporcionan los registros para ayudarte a encontrar la causa?

```bash
#Listamos todos los inicios del sistema
journalctl --list-boots

# Buscamos los logs de error en el servicio de nginx
journalctl -u nginx.service -b 24 -p3 -xe
```

### Notas Relacionadas
[[comandos-linux]]
[[Sistema de archivos]]
[[journald]]
[[journalctl logs de error]]
