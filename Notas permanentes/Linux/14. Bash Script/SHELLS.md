Tipo: Nota permanente
Fecha: 2026-08-21
Referencias:
* #Bash-script #Linux 
Temas: 
### ¿Que son las SHELLS?
La shell es un programa que nos permite transformar los comandos que escribimos en el teclado, en instrucciones que puedan ser utilizadas por nuestro computador para ejecutar una tarea en especifico, ya sea comandos nativos o scripts que nosotros mismos hemos creado.
La shell se encarga de establecer una comunicación entre el nucleo del sistema, es decir el kernel de linux y el usuario, sirviendo como una interfaz que nos permite interactuar con nuestro sistema operativo.

### Bash y otras shells
Bash es la shell estándar que se encuentra en la mayoría de las distribuciones linux del mundo, esto lo podemos comprobar al imprimir en consola la variable de entorno $SHELL.
```bash
echo $SHELL
# /bin/bash
```

**¿Que hay de otras shell?**
En la carpeta /etc existe un archivo llamado shells, este archivo contiene una lista de todas las shells disponibles en nuestro sistema.
```bash
cat /etc/shells
# /etc/shells: valid login shells
/bin/sh # Shell estandar predecesora de bash
/usr/bin/sh
/bin/bash # Shell avanzada para uso interactivo y scripting
/usr/bin/bash
/bin/rbash # Bash en modo restringido para limitar ciertas acciones
/usr/bin/rbash
/usr/bin/dash # Shell ligera y rapida para ejecutar scripts POSIX
/usr/bin/screen # Manejo de sesiones de terminal

```


### Notas Relacionadas
[[Variables de entorno]]
[[chsh]]
