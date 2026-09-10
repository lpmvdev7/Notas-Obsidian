Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-27
Referencias:
*  https://youtu.be/SLXYEnqmEgU?si=TJvFNNgsIT6dfNqm
Temas:  #Archivos #Linux 
### Sobre las acciones con archivos usando find
El comando find nos permite realizar acciones sobre los archivos o directorios que queremos encontrar, esto quiere decir que podemos ejecutar comandos sobre aquellos que cumpla las condiciones de nuestras consultas.
Las expresiones de find que nos permiten ejecutar acciones sobre archivos y carpetas son las siguientes:
* **-exec**: expresión que nos permite ejecutar comandos sobre los archivos o directorios que encontramos, esta opción en mi opinión es la mejor que tiene el comando find para ofrecer.
* **-delete** Eliminar archivos y directorios usando find
* **-print**: Expresión cuya función es imprimir la ruta del archivo o directorio encontrado.
* **-printf**: Expresión que nos permite personalizar el mensaje que se muestra en consola.
### Casos de uso 

#### -exec
Durante una auditoria se detecto que cientos de archivos de configuración (.conf) fueron modificados manualmente. Antes de desplegar una nueva versión de la aplicación, todos esos archivos deben convertirse automáticamente en respaldos con extensión .bak, conservando el contenido original.
La búsqueda debe realizarse en: **/etc**
```bash
find /etc -name "*.conf" -exec mv {} {}.bak \;
```

#### -delete
El servidor almacena miles de archivos temporales generados durante la compilación de proyectos. Para liberar espacio, el administrador debe eliminar todos los archivos con extensión .tmp que no hayan sido modificados en los últimos 15 días.
La búsqueda comienza en: **/home/build**
```bash
find /home/build -type f -name "*.tmp" -mtime +15 -delete
```

#### -print
El administrador del sistema necesita que borremos todos los archivos .bak y ademas mostremos en consola el nombre de esos archivos que estamos eliminando.
```bash
# Borra los archivos .bak Y ADEMÁS imprime sus nombres según los borra:
find . -type f -name "*.bak" -print -delete
```

#### -printf
El líder del equipo quiere revisar que archivos de configuración existen en el servidor y quien es el propietario de cada uno.
Debes buscar todos los archivos con extensión .conf en el directorio /etc.
Por cada archivo encontrado, el reporte debe mostrar:
* La ruta completa del archivo
* El usuario propietario.
```bash
find /etc -type f -name "*.conf" -printf "Ruta: %p | dueño: %u\n"
```
#### Caso de uso unificado
Cada domingo por la noche se ejecuta una tarea de mantenimiento sobre el servidor de aplicaciones.
El administrador necesita:
* Buscar archivos .log
* Que sean mayores de 500MB
* Modificados hace mas de 60 días
* Pertenecientes al usuario nginx
* Excluir cualquier directorio llamado backup
* Comprimir cada archivo utilizando gzip
La búsqueda comienza en: **/var/log**
```bash
find /var/log -path "*/backup" -prune -o -type f -name "*.log" -size +500M -mtime +60 -user nginx -exec gzip {}\; 
```
### Notas Relacionadas
[[find]]
[[find - expresiones de busqueda]]
[[find - expresiones de filtrado]]
[[find - expresiones de recorrido]]
[[find - uso de operadores logicos]]
