Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-27
Referencias:
* https://youtu.be/SLXYEnqmEgU?si=TJvFNNgsIT6dfNqm
Temas: #Archivos #Linux 
### ¿Para que sirven las expresiones de recorrido? 
Las expresiones de recorrido en el comando find son aquellas que nos ayudan a modificar el comportamiento de find a la hora de recorrer una ruta.
Las expresiones de recorrido son las siguientes:
* -maxdepth: Modificar la profundidad máxima en la que el comando find puede buscar un archivo.
* min-depth: Modificar la profundidad mínima desde la cual el comando find puede empezar a buscar un archivo o directorio
* -prune: Evitar que la búsqueda vaya a un directorio que nosotros especificamos.

### Casos de uso para las expresiones de recorrido
#### -maxdepth
La empresa guarda sus proyectos en la ruta **/proyectos**, la cual tiene la siguiente estructura:
```bash
/proyectos
│
├── PortalVentas
│   ├── src
│   ├── docs
│   └── assets
│
├── PortalCompras
│   ├── src
│   └── docs
│
└── PortalInventario
    ├── src
    └── assets
```
El directorio de infraestructura quiere saber que proyectos existen, pero no le interesa ver el contenido de cada proyecto.
```bash
find /proyectos -type d -maxdepth 1
```

#### -mindepth
La empresa GreenData tiene el siguiente repositorio:
```bash
/respaldos
│
├── enero
├── febrero
├── marzo
│   ├── semana1
│   ├── semana2
│   └── semana3
```
El administrador quiere obtener un listado de todos los directorios de respaldo, pero no desea que aparezca el propio directorio /respaldos, ya que sabe desde donde esta ejecutando el comando.
```bash
find /respaldos -type d -mindepth 1
```

#### -prune
En un servidor existen decenas de aplicaciones web.
Cada una posee una carpeta llamada cache que contiene miles de archivos temporales.
```bash
/var/www
│
├── PortalVentas
│   ├── cache
│   └── src
│
├── PortalCompras
│   ├── cache
│   └── src
│
└── PortalRH
    ├── cache
    └── src
```
Necesitamos buscar todos los archivos PHP del servidor.
Sin embargo, las carpetas cache contiene millones de archivos temporales y no deben recorrerse, ya que ralentizarían enormemente la búsqueda.
Nuestra misión aquí es impedir que find entre a cualquier directorio llamado cache.
```bash
find /var/www -path "*/cache" -prune -o -type f -name "*.php"
```

#### Caso de uso unificado
La empresa TechNova almacena todas sus aplicaciones en la siguiente estructura de carpetas:
```bash
/opt/apps
│
├── PortalVentas
│   ├── cache
│   ├── src
│   └── config
│
├── PortalCompras
│   ├── cache
│   ├── src
│   └── config
│
├── PortalRH
│   ├── cache
│   ├── src
│   └── config
│
└── backups
    └── ...
```
Se nos ha encargado la tarea de localizar todos los archivos .conf, cumpliendo con las siguientes reglas:
1. La búsqueda debe comenzar en /opt/apps
2. No se debe considerar el propio directorio /op/apps
3. No se deben recorrer mas de tres niveles de profundidad
4. Nunca se debe entrar en directorios llamados cache
5. Debes mostrar únicamente los archivos .conf
```bash
find /opt/apps -mindepth 1 -maxdepth 3 -path "*/cache" -prune -o -type f -name "*.conf"
```

### Notas Relacionadas
[[find]]
[[find - expresiones de busqueda]]
[[find - expresiones de filtrado]]
[[find - uso de operadores logicos]]
[[find - acciones sobre archivos]]


[^1]: 
