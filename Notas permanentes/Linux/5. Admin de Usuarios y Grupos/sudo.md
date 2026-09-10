Tipo: Nota permanente
Fecha: 2026-07-21
Referencias:
* https://www.youtube.com/watch?v=Hc9Tfr3tY_A 
* Linux.pdf
Temas:  #Comandos #Permisos #usuarios #grupos 
### ¿Que es sudo?
sudo es un comando en linux que permite a otros usuarios del sistema operativo tener capacidades administrativas.
Es el comando que nos permite convertirnos por un momento en el usuario root, por lo que se debe usar cuidadosamente.

### Sintaxis de uso
El comando se utiliza colocando la palabra **sudo** al inicio del comando que queramos ejecutar.  
```bash
sudo cat
```

### El grupo sudo
El grupo sudo es el conjunto de usuarios que pueden ejecutar el comando sudo, siempre y cuando exista una instrucción en un archivo llamado sudoers que se los permita.
```bash
sudo:x:27:ubuntu,pablo
```

### El archivo sudoers
Sudoers es el archivo en el cual se asignan los permisos del comando sudo, aquí definimos que usuarios del sistema pueden utilizar el comando sudo, e incluso podemos restringir su uso solo para comandos específicos.

Definimos el uso del comando sudo mediante instrucciones con la siguiente sintaxis:
```bash
username    host=(usuario_efectivo:grupo_efectivo) comandos
```

Estas instrucciones nos permiten otorgar permisos sobre el comando sudo a usuarios y grupos, controlando que comandos pueden ejecutar ciertos usuarios o ciertos grupos de usuarios.
#### Ubicación
El archivos sudoers se encuentra en la siguiente ruta del sistema de archivos:
```bash
/etc/sudoers
```

#### Modificando el archivo sudoers
El archivo sudoers puede ser modificado mediante el comando **visudo**

**¿Que es visudo?**
El comando visudo abre el archivo sudoers en el editor de texto de nuestra preferencia, pero con la particularidad de que nos cuida de todos aquellos errores de sintaxis que pueden dejar el archivo inutil.

## Ejemplo
>En una empresa existe un servidor Linux utilizado por varios desarrolladores.
>Se decide crear un grupo llamado desarrolladores. Todos los programadores de la empresa pertenecen a este grupo.
>Por motivos de seguridad, la empresa no quiere que los desarrolladores tengan acceso completo mediante **sudo**. Sin embargo necesitan poder reiniciar el servicio de la aplicación cuando despliegan una nueva versión.
>El administrador del sistema debe configurar el servidor para que:
>1. Los usuarios pertenecientes al grupo de desarrolladores puedan ejecutar únicamente el comando necesario para reiniciar el servicio de la aplicación utilizando sudo
>2. Cualquier otro comando ejecutado con sudo por esos usuarios debe ser rechazado
>3. Los usuarios que no pertenezcan al grupo desarrolladores no deben poder reiniciar el servicio.

### Paso 1
Para el paso 1 crearemos un script que simule el reinicio de un servicio. Es importante que coloquemos este script en una carpeta reconocible para la variable de entorno PATH.
```bash
#!/bin/bash
echo "Reiniciando servicio...."
sleep 2s
echo "Servicio reiniciado exitosamente"
```

### Paso 2
Ahora crearemos un grupo llamado desarrolladores
```bash 
groupadd desarrolladores
```

### Paso 3
Creamos un usuario llamado pablo y lo asignamos al grupo de desarrolladores.
```bash
useradd -G desarrolladores pablo
```

### Paso 4
Ahora nos dirigimos al archivo sudoers y creamos una regla que especifique que solo los usuarios de el grupo de desarrolladores podrán ejecutar el comando junto con sudo.
```bash
%desarrolladores ALL=(ALL:desarrolladores) /usr/local/bin/reinicioService.sh
```

### Paso 5
Iniciamos sesión con el usuario pablo y tratamos de ejecutar el comando con sudo.
```bash
sudo reinicioService.sh
Reiniciando servicio....
Servicio reiniciado exitosamente
```

También podemos comprobar que ese es el único comando que podemos ejecutar como root, si intentamos con cualquier otro no funcionara.
```bash
sudo mkdir 
Sorry, user pablo is not allowed to execute '/usr/bin/mkdir' as root on 382fe80dff5c.
```

### Paso Final
Por ultimo iniciamos sesión con un usuario que no pertenezca  al grupo desarrolladores e intentamos ejecutar el comando, si todo esta correcto ese usuario no podra ejecutar ese comando con sudo.
```bash
$ sudo reiniciandoService.sh
[sudo] password for luis: 
luis is not in the sudoers file.
```

### Notas Relacionadas
[[Usuarios]]
[[Grupos]]
[[Bash Scripting]]
[[Permisos en Linux]]
