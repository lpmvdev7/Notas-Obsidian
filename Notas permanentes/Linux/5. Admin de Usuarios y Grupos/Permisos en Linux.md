Tipo: Nota permanente
Fecha: 2026-07-22
Referencias:
* Linux.pdf 
Temas:  #Archivos #grupos #usuarios #Permisos 
### ¿Para que sirven los permisos en Linux?
Los permisos en linux sirven para poder controlar que usuarios y grupos tienen acceso a ciertos archivos. Nos ayudan a evitar que usuarios pertenecientes a cierto grupo puedan leer archivos que podrían considerarse confidenciales y hasta incluso nos permiten configurar el servidor de tal manera que ciertos usuarios no puedan ejecutar determinados scripts.
A mi consideración los permisos son un mecanismo de seguridad a nivel administrativo en linux que nos permite asignar acciones especificas de los usuarios sobre los recursos del sistema.

### Tipos de permiso 
En linux existen tres tipos de permiso que se le pueden aplicar a un archivo
* Read (r): Permisos de lectura sobre un archivo
* Write (w): Permisos de escritura sobre un archivo
* Execute (x): Permisos de ejecución de un archivo

### Obtener información sobre permisos
Estos permisos sobre los archivos se hacen presentes cuando ejecutamos el comando **ls-l**.
```bash
ls -l
total 30860
-rw-r--r-- 1 root  root       485 feb 16 23:01 backup-repos.list
drwxrwxr-x 3 pablo pablo     4096 may  9 09:44 Base-de-datos-restaurante
```

Al ejecutar el comando **ls-l** podemos ver que se nos muestra la información completa relacionada a un archivo o directorio, en la siguiente imagen podemos ver una explicación de que es lo que muestra **ls -l** y porque es relevante para aprender permisos en linux.
![[explicacion-informacion-archivo|1000]]

Como podemos ver en la siguiente imagen los permisos se componen de tres grupos diferentes:
* Owner
* Group
* Other
![[permisos-explicacion|1000]] 

### Comandos que nos ayudan a modificar permisos
En linux existen dos comandos que nos ayudan a modificar permisos:
* chmod: cambiar los permisos de un archivo
* chown: cambiar a los dueños de un archivo.
### Notas Relacionadas
[[Grupos]]
[[Usuarios]]
[[ls]]
[[chmod]]
[[chown]]


