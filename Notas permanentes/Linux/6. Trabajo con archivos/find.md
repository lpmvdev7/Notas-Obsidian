Tipo: Nota permanente
Fecha: 2026-07-24
Referencias:
* https://youtu.be/SLXYEnqmEgU?si=TJvFNNgsIT6dfNqm
Temas: #Archivos #Linux 
### ¿Que hace el comando find?
El comando find es la instrucción definitiva para encontrar archivos en linux, su gran variedad de opciones nos permite encontrar cualquier archivo dentro del sistema de archivo dado ciertos criterios de búsqueda que nosotros manipulamos

### Uso del comando
La sintaxis normal para el comando find es la siguiente:
```bash
find [directorio] [expresiones]
```

### ¿Como funciona el comando find?
Como pudimos ver en la sintaxis de arriba, el comando find necesita de dos argumentos principalmente para funcionar (en la practica estos argumentos pueden ser mas), el directorio y las expresiones.
Cuando ejecutamos el comando ocurre lo siguiente:
1. Find recorre la estructura de la carpeta que hemos indicado
2. Por cada elemento dentro de esa estructura ejecuta la expresión que le hemos indicado.

### Expresiones con el comando find
El comando find tiene una gran variedad de expresiones que nos pueden ayudar a aplicar sin fin de condiciones a la hora de buscar archivos o directorios.
A continuación mencionamos algunas:

#### 1. Expresiones de búsqueda
* **-name**
* **-iname**
* **-path**
* **-regex**
#### 2. Expresiones de filtrado
* **-type**
* **-size**
* **-empty**
* **-mtime**
* **-perm**
* **-user**
* **-group**

#### 3. Expresiones de recorrido
* **-maxdepth**
* **-mindepth**
* **-prune**

#### 4. Operadores lógicos
* **NOT
* **AND
* **OR

#### 5. Acciones sobre archivos
* **-exec**
* **-delete**
* **print**: 
* **printf**: 
### Casos de uso del comando find
#### Búsqueda de respaldos antiguos 
El servidor almacena respaldos de bases de datos.
Necesita localizar todos los archivos .sql en la carpeta /backups que:
* Sean archivos normales
* Midan mas de 50 MB
* Fueron modificados hace mas de 15 días.
```bash
find /backups -type f -size +50M -mtime +15
```

#### Excluir un directorio
Los desarrolladores quieren localizar todos los archivos JavaScript.
Sin embargo, la carpeta node_modules no debe recorrerse porque contiene miles de dependencias.
Debes:
* Buscar archivos únicamente
* Que terminen en .js
* Excluir cualquier directorio llamado node_modules
La búsqueda comienza en: **/proyectos**
```bash
find /proyectos -path "*/node_modules" -prune -o -type f -name "*.js" 
```

#### Auditoria de permisos
Se deben localizar los archivos que cumplan con las siguientes caracteristicas:
* Sean archivos normales
* Tengan permisos 777
* Pertenezcan al usuario www-data
* Midan mas de 5MB
* Se tiene que mostrar la ruta completa del archivo
La busqueda comienza en: /var/www
```bash
find /var/www -type f -perm 777 -user www-data -size +5M -print
```

#### Limpieza de archivos temporales
El administrador quiere eliminar archivos temporales que cumplan las siguientes condiciones:
- Sean archivos normales
- Terminen en .tmp
- Fueron modificados hace mas de 30 dias
- No pertenecen al usuario root
- Eliminarlos
La búsqueda comienza en: /tmp
```bash
find /tmp -type f -name "*.tmp" -mtime +30 ! -user root -exec rm {} \;
```

#### Configuración de un servidor
Necesitas localizar archivos de configuración que cumplan:
* Sean archivos normales
* Terminen en .conf o .cfg
* Midan menos de 1 MB
* Pertenezcan al grupo apache
* No entrar en ningún directorio llamado backup
* Imprimir la ruta de cada archivo encontrado
La búsqueda comienza en: **/etc**
```bash
find /etc -path "*/backup" -prune -o -type f -size -1M -group apache \( -name "*.conf" -o -name "*.cfg"\)
```

### Notas Relacionadas
[[comandos-linux]]
[[find - expresiones de busqueda]]
[[find - expresiones de filtrado]]
[[find - expresiones de recorrido]]
[[find - uso de operadores logicos]]
[[find - acciones sobre archivos]]
