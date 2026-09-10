Tipo: Nota permanente
Fecha: 2026-07-22
Referencias:
* Linux.pdf
* https://manned.org/useradd
Temas: #usuarios #Linux #Comandos 
### ¿Que hace el comando useradd?
El comando useradd nos permite crear un usuario en sistemas linux.

### Uso del comando
```bash
 - Crea un usuario:
   sudo useradd usuario

 - Crea un usuario con el ID de usuario específico:
   sudo useradd [-u|--uid] id usuario

 - Crea un usuario con una línea de comando (shell) específica:
   sudo useradd [-s|--shell] ruta/a/la/shell usuario

 - Crea un usuario perteneciente a grupos adicionales (ten en cuenta que no se colocan espacios en blanco):
   sudo useradd [-G|--groups] grupo1,grupo2,... usuario

 - Crea un usuario con el directorio home predeterminado:
   sudo useradd [-m|--create-home] usuario

 - Crea un usuario con el directorio home con una copia de los archivos provenientes de un directorio plantilla:
   sudo useradd [-k|--skel] ruta/a/directorio_plantilla [-m|--create-home] usuario

 - Crea un usuario del sistema sin directorio home:
   sudo useradd [-r|--system] usuario
```

### Ejemplo con caso de uso
 El lunes se integra una nueva desarrolladora al equipo. Necesita conectarse al servidor para empezar a realizar sus tareas y necesita tener un espacio en donde guardar sus archivos.

#### Solución al caso de uso
Al leer el enunciado lo primero que tenemos que hacer es identificar el problema y escribir como podríamos resolverlo con nuestros conocimientos.

>"El usuario necesita que nosotros como administradores de servidores creemos un nuevo usuario el cual tenga su propio directorio home."

Una vez escribimos como podríamos resolver el problema, pensamos en la serie de pasos que necesitamos completar para  resolver el problema.
1. Asignar un nombre al usuario
2. Asignarle un directorio home
3. Asignarle una shell, para la ejecución de comandos.

```bash
sudo useradd pablo -m -s /bin/bash
```

#### Explicación de la solución
Utilizamos el comando useradd como solución a la problemática planteada, usando las opciones -m y -s, le asignamos un directorio home y un interprete de comandos al nuevo usuario respectivamente.



### Notas Relacionadas
[[Usuarios]]
[[comandos-linux]]
[[userdel]]
[[usermod]]
[[who]]
[[passwd]]
