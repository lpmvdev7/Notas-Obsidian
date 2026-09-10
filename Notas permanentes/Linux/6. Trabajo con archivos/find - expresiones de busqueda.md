Tipo: Nota permanente
Fecha: 2026-07-27
Referencias:
* https://youtu.be/SLXYEnqmEgU?si=TJvFNNgsIT6dfNqm
Temas:  #Archivos #Linux 
### ¿Que son las expresiones de búsqueda en el comando find?
En el comando find si bien todas las expresiones que utilizamos nos ayudan a encontrar archivos, las expresiones de búsqueda destacan de entre toda debido a la precisión con la cual podemos modificar nuestros parámetros en pro de encontrar un archivo o directorio.
Con las expresiones de búsqueda podemos casi casi decir que archivo estamos buscando.
Algunas de estas expresiones son:
1. **-name**: Nos permite buscar un archivo por su nombre 
2. **-iname**: Nos permite buscar un archivo por su nombre sin importar si el nombre a buscar esta en mayúscula o minúscula.
3. **-path**: Especificamos una ruta completa en la cual buscar.
4. **-regex**: Encontrar archivos o directorios cuya ruta completa coincida con una expresión regular.

### Casos de uso para cada expresión de búsqueda
#### -name
Trabajamos como administradores de sistemas en una empresa de desarrollo de software. Un desarrollador nos reporta que accidentalmente ha modificado el archivo config.php, pero no recuerda en cual de los mas de 50 proyectos alojados en el servidor se encuentra.  Nuestra tarea consiste en localizar todos los archivos llamados config.php para identificar cual fue modificado

```bash
find . -name "config.php"
```

#### -iname
La empresa ha migrado miles de fotografías provenientes de distintos sistemas operativos. Algunos usuarios guardaron imágenes como VACACIONES.JPG, otros como vacaciones.jpg y otros como Vacaciones.Jpg. El departamento de marketing necesita localizar todas las imágenes JPG sin importar como este escrita la extensión.

```bash
find . -iname "vacaciones.jpg"
```

#### -cache
Administras un servidor donde se alojan varias aplicaciones web. Cada aplicación posee un directorio llamado cache, el cual debe vaciarse antes de desplegar una nueva versión. Antes de eliminar su contenido, deseas localizar únicamente los archivos que se encuentran dentro de cualquier directorio llamado cache, sin importar a que aplicación pertenezcan.
```bash
find . -path "*/cache"
```

#### -regex
Una empresa genera respaldos automáticos de sus bases de datos con el siguiente formato:
```bash
ventas_20260725.sql
ventas_20260726.sql
ventas_20260727.sql
clientes_20260727.sql
```
El administrador necesita localizar únicamente los respaldos de la base de datos ventas cuyo nombre siga exactamente el patrón ventas_YYYMMDD.sql, descartando cualquier otro archivo con nombres similares. 
```bash
find . -regex ".*/ventas_[0-9]\{8\}\.sql"
```

### Notas Relacionadas
[[find - expresiones de filtrado]]
[[find - expresiones de recorrido]]
[[find - uso de operadores logicos]]
[[find - acciones sobre archivos]]


