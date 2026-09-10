Tipo: Nota permanente
Fecha: 2026-07-16
Referencias:
* Linux.pdf
Temas:  #Linux #OS #Archivos #Comandos #Variables-entorno 
### ¿Que es la variable PATH y porque es importante?
La variable $PATH es muy importante en sistemas Linux ya que en ella se listan todos los directorios que contienen ejecutables dentro de nuestro sistema de archivos.

En el siguiente ejemplo podemos ver el contenido de la variable $PATH, pero realmente que es lo que estamos viendo.
```bash
PATH=/home/pablo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/opt/node/bin
```

Lo que estamos viendo son rutas a directorios dentro de nuestro sistema de archivos, cada una de esas rutas apuntan a directorios que contienen ejecutables dentro de nuestro sistema, siendo esos ejecutables los comandos que utilizamos para nuestras tareas diarias como ingenieros de software, ingenieros de datos o ingenieros de nube.

### El viaje de un comando para ejecutarse en el sistema.
1. Elegimos el comando a ejecutar ls
2. Tecleamos el comando en la terminal
3. El shell consulta la variable de entorno $PATH
4. El shell viaja a cada directorio listado en la variable $PATH
5. El shell encuentra el ejecutable de ls y ejecuta nuestra indicacion

![[Diagrama-flujo-PATH]]

### ¿Se puede modificar la variable PATH?
Si, la variable PATH se puede modificar, esto es muy importante dado que como superusuarios de linux en muchas ocasiones nos vamos a encontrar con lo siguiente:
1. Repetimos un proceso muchas veces
2. Queremos simplificar ese proceso
3. Creamos un script para simplificar el proceso
El tema aquí, es que cuando creamos el script lo colocamos en un directorio que no se encuentra listado en el PATH, esto en si no es problema ya que siempre podemos ir al directorio para ejecutar el script, pero que hueva hacer esto una y otra vez nmms,  lo que podemos hacer es listar ese directorio en el PATH y de esa manera el script sera accesible GLOBALMENTE en nuestro sistema.

### ¿Como modifico la variable PATH?
Cuando imprimimos la variable PATH con el comando echo, podremos notar que esta tiene una sintaxis cuanto menos particular.
```bash
echo $PATH
/home/pablo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/opt/node/bin
```
Podemos notar la presencia de muchos :, estos sirven como separador, es decir como si fuera una coma.

#### Editando PATH
Creamos una carpeta llamada scripts
```bash
mkdir scripts
```

Ahora modificamos PATH para que tome la carpeta scripts como directorio en el cual buscar ejecutables del sistema.
```bash
export PATH="$PATH:$HOME/scripts"
```

Al imprimir PATH con echo podemos ver que nuestro nuevo directorio ha sido añadido.
```bash
echo $PATH 
/home/pablo/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/opt/node/bin:/home/pablo/scripts
```
### Notas Relacionadas
[[Variables de entorno]]
[[Diagrama-flujo-PATH]]
[[Sistema de archivos]]
[[Bash Scripting]]
[[echo]]
