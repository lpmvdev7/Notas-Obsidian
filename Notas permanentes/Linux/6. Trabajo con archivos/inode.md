Tipo: Nota permanente
Fecha: 2026-07-24
Referencias:
* 
Temas: #links #Linux #Archivos  
### ¿Que es un inode?
Un inode es una estructura de datos que almacena toda la información de un archivo o directorio, excepto su nombre.
Si nosotros como personas identificamos los archivos mediante su nombre, el sistema operativo lo hace mediante los inode.
### ¿Que info almacena el inode?
El inode se encarga de almacenar metadatos como:
* Tipo de archivo (archivo, directorio, enlace)
* Permisos
* Propietario
* Grupo
* Tamaño del archivo
* Fechas de creación, ultima modificación y ultimo acceso
* El numero de hard links del archivo
* Ubicación de los bloques de datos en el disco.

### Como puedo ver un inode
En linux podemos interactuar con los inodes de muchas maneras, algunas de las que conozco al momento de escribir estas notas son las siguientes:
* stat
```bash
stat backup-repos.list 
  Fichero: backup-repos.list
  Tamaño: 485       	Bloques: 8          Bloque E/S: 4096   fichero regular
Device: 259,5	Inode: 11630943    Links: 1
Acceso: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Acceso: 2026-07-21 16:45:19.572086628 -0600
Modificación: 2026-02-16 23:01:28.566907175 -0600
      Cambio: 2026-02-16 23:01:28.566907175 -0600
    Creación: 2026-02-16 23:01:28.565854830 -0600

```
* ls -li
```bash
ls -li backup-repos.list 
11630943 -rw-r--r-- 1 root root 485 feb 16 23:01 backup-repos.list
```
* find: este es especialmente útil porque nos ayuda a ver todos los archivos que apuntan a un mismo inode.
```bash
find -inum 11630943
./backup-repos.list
```

### Notas Relacionadas
[[stat]]
[[find]]
[[Hard-links]]
[[Soft-links]]

