Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-27
Referencias:
* https://youtu.be/SLXYEnqmEgU?si=TJvFNNgsIT6dfNqm
Temas: #Archivos #Linux  
### ¿Que son las expresiones de filtrado en el comando find?
Las expresiones de filtrado en el comando find nos ayudan a enriquecer nuestra búsqueda de archivos o directorios permitiéndonos ser mas precisos sobre lo que estamos buscando.
Las expresiones de filtrado utilizando find serian las siguientes:
* **-type**: Buscar archivos, directorios y enlaces simbolicos.
* **-size**: Encontrar un archivo o directorio por su tamaño
* **-empty**: Encontrar aquellos archivos o directorios que se encuentran vacíos.
* **-mtime**: Encontrar los archivos o directorios que han sido modificados en los dias que indiquemos.
* **-perm**: Encontrar archivos o directorios basado en los permisos que estos tienen.
* **-user**: Encontrar los archivos pertenecientes a un usuario.
* **-group**: Encontrar los archivos pertenecientes a un grupo.

### Casos de uso para cada expresión de filtrado
#### -type
Trabajamos como administrador de un servidor linux que aloja varias aplicaciones web. Antes de realizar un respaldo, necesitamos obtener una lista de todos los directorios del proyecto para verificar que la estructura sea correcta, sin mostrar archivos ni enlaces simbólicos.
```bash
find . -type d 
```

#### -size
El servidor de producción se esta quedando sin espacio en disco. Sospechas que algunos archivos de registro han crecido demasiado y quieres localizar todos los archivos que ocupen mas de 500MB dentro de /var/log.
```bash
find /var/log -type f -size +500M
```

#### -empty
Después de eliminar miles de archivos temporales, deseas localizar todos los directorios vacíos que quedaron para decidir si deben eliminarse o mantenerse.
```bash
find . -type d -empty
```

#### mtime
La empresa tiene una política de respaldar únicamente los archivos que fueron modificados durante el ultimo día. Necesitas localizar esos archivos dentro del directorio /var/www
```bash
find . -type f -mtime -1
```

### -perm
Durante una auditoria de seguridad debes localizar todos los archivos que tengan permisos 777, ya que representan un riesgo potencial
```bash
find . -type f -perm 777 
```

#### -user
Una empleada llamada laura dejo la empresa. Antes de eliminar su cuenta, necesitas localizar todos los archivos que aun son propiedad de ese usuario.
```bash
find . -user laura 2>/dev/null
```

#### -group
El equipo desarrolladores sera migrado a un nuevo grupo. Antes de realizar el cambio, necesitas localizar todos los archivos que pertenecen actualmente a dicho grupo.
```bash
find . -group desarrolladores
```

#### Caso de uso unificado para las expresiones de filtrado
FinCloud  Solutions desarrolla software para instituciones financieras y almacena documentos internos, reportes y respaldos en un servidor Linux.
Durante una auditoria de seguridad y almacenamiento, el gerente de infraestructura te solicita generar un reporte con todos los archivos que cumplen las siguientes condiciones.
* Son archivos normales (no directorios ni enlaces simbólicos)
* Ocupan mas de 200MB
* No están vacíos
* Fueron modificados hace mas de 90 días
* Tienen permisos 777, ya que representan un riesgo de seguridad
* Pertenecen al usuario Juan
* Ademas, pertenecen al grupo contabilidad.
La búsqueda debe realizarse en la siguiente ruta: **/empresa**
```bash
find /empresa -type f -size +200M -mtime +90 -perm 777 -user Juan -group contabilidad
```

### Notas Relacionadas
[[find]]
[[find - expresiones de busqueda]]
[[find - expresiones de recorrido]]
[[find - uso de operadores logicos]]
[[find - acciones sobre archivos]]



