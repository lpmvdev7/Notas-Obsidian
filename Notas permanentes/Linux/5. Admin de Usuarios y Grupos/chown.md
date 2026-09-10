Tipo: Nota permanente
Fecha: 2026-07-23
Referencias:
* Linux.pdf
Temas: #Archivos #Comandos #Permisos 
### El comando chown
El comando chown se encarga de cambiar al usuario y al grupo dueño de un archivo.

### Uso del comando chown
Existen varias formas de usar el comando chown dependiendo de lo que queramos hacer.

Esta es la sintaxis que deberíamos seguir si queremos cambiar al usuario propietario de un archivo.
```bash
chown usuario archivo
```

Esta sintaxis la deberíamos usar en todos aquellos casos en los que necesitemos únicamente cambiar el grupo propietario de un archivo.
```bash
chown :grupo archivo
```

Esta otra sintaxis la deberíamos seguir si queremos cambiar tanto al usuario como al grupo propietario de un archivo.
```bash
chown usuario:grupo archivo
```

En muchos casos nos veremos en la necesidad de cambiar a los dueños de un directorio, en la mayoría de casos esos directorios le pertenecerán al mismo dueño, es por eso que para ahorrarnos el estar cambiando el dueño archivo por archivo, deberíamos usar esta sintaxis.

```bash
chown -R usuario directorio
```

### Caso de uso comando chown
> La empresa TechSolutions desarrolla aplicaciones web para distintos clientes. Cada proyecto se almacena en un servidor linux dentro del directorio /var/www
> Pedro, el desarrollado backend responsable de un proyecto llamado **PortalVentas**, dejo la empresa. Como parte del proceso de transición, Laura ha sido asignada como la nueva responsable del proyecto.
> Aunque Laura ya tiene una cuenta en el servidor, todos los archivos del proyecto siguen perteneciendo a Pedro, lo que impide que Laura pueda administrar correctamente el codigo y realizar despliegues.
> Como administrador de sistemas, debes transferir la propiedad del directorio **PortalVentas** y de todos los archivos y subdirectorios que contiene para que Laura sea la nueva propietaria del proyecto.

#### Solución
```bash
sudo chown -R laura /var/www/PortalVentas
```

### Notas Relacionadas
[[Usuarios]]
[[Grupos]]
[[comandos-linux]]
[[chmod]]

