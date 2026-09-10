Tipo: Nota permanente
Fecha: 2026-08-06
Referencias:
* Linux.pdf
Temas: #filesystem
### ¿Que es un sistema de archivos?
Un sistema de archivos es la forma que utiliza el sistema operativo utiliza para organizar, almacenar y administrar datos en un dispositivo de almacenamiento (disco duro, SSD, USB, etc)
Los sistemas de archivos son estructuras jerárquicas que permiten guardar, acceder, modificar y eliminar archivos y directorios.

### ¿Como funciona el sistema de archivos en linux?
El sistema de archivos en linux se organiza mediante una jerarquia parecida a la de un arbol, en la cual la rama padre es el directorio root.
De root se bifurcan varios directorios que contienen funciones esenciales para el funcionamiento del sistema operativo.

#### Directorio /bin
```bash
cd /bin
```
En el directorio bin se encuentran todos los ejecutables del sistema, aqui viven los comandos que utilizamos al ejecutar tareas en la terminal, utilidades como ls, pwd, mkdir, rmidr y muchos otros mas viven en este directorio. 

#### Directorio /boot
```bash
cd /boot
```
En este directorio viven todos aquellos archivos dedicados a iniciar el sistema.

#### Directorio /dev
```bash
cd /dev
```
En este directorio se registran archivos relacionados a un dispositivo de hardware, como sabemos un pc esta compuesto de varias piezas, esas piezas en el mundo linux generan archivos los cuales viven en este directorio.

#### Directorio /etc
```bash
cd /etc
```
En este directorio viven las configuraciones de nuestro sistema, así como registros de administración de usuarios y grupos como el archivo passwd o group. Su nombre es "Everything to configure"

#### Directorio /home
```bash
cd /home/pablo
```
Directorio principal de un usuario, aquí viven todos aquellos directorios que un usuario utiliza en su día a día, folders como Escritorio, Descargas, Música o Documentos viven aquí.

#### Directorio /lib
```bash
cd /lib
```
Aquí viven todas las librerías que el sistema operativo utiliza para su funcionamiento. 

#### Directorio /media
```bash
cd /media
```
Cuando conectamos almacenamiento externo al computador, se monta en este directorio.

#### Directorio /mnt
```bash
cd /mnt
```
Directorio en el que se montan las particiones de almacenamiento.

#### Directorio /opt
```bash
cd /opt
```
Directorio en donde se ubica el software que compilas (software que creas tu mismo a partir del codigo fuente y no lo instalas desde los repos oficiales de la distribuciones)

#### Directorio /proc
```bash
cd /proc
```
Directorio de archivos virtuales que contienen informacion sobre los procesos que ocurren en el computador.

#### Directorio /
```bash
cd /
```
Directorio inicial del superusuario

#### Directorio /run
```bash
cd /run
```
Directorio que almacena datos de tiempo de ejecución que no necesitan persistir tras los reinicios del sistema.

#### Directorio /sbin
Directorio que contiene los ejecutables que el superusuario necesitara, es decir aquellos comandos que al ejecutarlos vengan acompañados de la palabra sudo.
```bash
cd /sbin
```

#### Directorio /usr
```bash
cd /usr
```
Directorio que almacena la mayoría de los programas, bibliotecas, documentación y archivos compartidos del sistema.

#### Directorio /srv
El directorio srv de service se encuentra vació, pero se usa para almacenar los datos que sirven los servicios del sistema, por ejemplo sitios web o repositorios git.
```bash
cd /srv
```

#### Directorio /sys
Directorio que contiene información de los dispositivos conectados a la computadora.
```bash
cd /sys
```

#### Directorio /tmp
Directorio que almacena los archivos temporales de las aplicaciones.
```bash
cd /tmp
```

#### Directorio /var
Directorio que contiene todos los registros del sistema, si ocurre una falla en el sistema se registrara en un archivo en /var/log
```bash
cd /var
```


![](https://i0.wp.com/blockstellart.com/wp-content/uploads/2025/01/Sistema-de-archivos-en-Linux-2.png?resize=1300%2C1400&ssl=1)

### Notas Relacionadas
[[Tipos de sistemas de archivos]]
[[PATH]]

