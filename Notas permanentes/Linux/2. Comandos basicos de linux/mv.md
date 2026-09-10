Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-15
Referencias:
* Linux.pdf
Temas:  #Comandos #Linux 
### ¿Que problema resuelve el comando mv?
El comando mv es un comando que nos ayuda a renombrar y mover archivos o directorios dentro de nuestro sistema de archivos.

#### ¿Como se usa?
En este ejemplo mostramos como el comando mv cambia el nombre de un archivo .txt
```bash
ls
archivito.txt

mv archivito.txt nuevo-nombre.txt

ls
nuevo-nombre.txt
``` 

En este otro mostramos como el comando mv tiene el poder de mover ese archivo hacia otra carpeta.

```bash
mv nuevo-nombre.txt /home/pablo

ls /home/pablo
nuevo-nombre.txt
```
### Notas Relacionadas
[[Sistema de archivos]]
[[comandos-linux]]
[[man]]
[[tldr]]
