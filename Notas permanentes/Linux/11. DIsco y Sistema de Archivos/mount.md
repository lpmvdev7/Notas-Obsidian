Tipo: Nota permanente
Fecha: 2026-08-06
Referencias:
* Linux.pdf
* https://phoenixnap.com/kb/linux-mount-command
Temas: #Almacenamiento #filesystem 

### ¿Que es montar?
Montar consiste en hacer accesible un sistema de archivos desde un punto determinado del árbol de directorios.

### ¿Que hace el comando?
El comando mount permite al usuario montar sistemas de archivos adicionales en un punto particular que sea accesible desde el sistema de archivos central.
El uso de este comando es esencial a la hora de trabajar como administradores de sistemas, ya que su correcto uso nos ayudara a realizar tareas de emergencia como la recuperación de información.

### Uso del comando
El comando mount nos puede ayudar tanto a montar sistemas de archivos como a ver información relevante relacionada a estos, por lo que su uso es muy variado.
```bash
# Listamos los sistemas de archivos montados
mount
```

```bash
# Con la opcion -t especificamos que se liste la info de un sistema de archivos
mount -t ext4
```

```bash
cd /mnt
mkdir media

# Montamos el sistema de archivos ext4 en /mnt/media
mount /dev/sda1 /mnt/media
cd media 
```

```bash
# Aqui estoy montando mi sistema de archivos entero en /mnt/media
sudo mount -t ext4 /dev/nvme0n1p5 /mnt/media/
```

>Algo que cabe aclarar, cuando montamos sistemas de archivos existentes en alguna otra carpeta de nuestro computador, no estamos creando una copia del sistema de archivos, lo que estamos haciendo es que ese sistema de archivos sea accesible desde otra ruta de nuestro computador.
>Es por esta razón que cualquier modificación que hagamos a los archivos en el nuevo punto de montaje, también se vera reflejada en la ubicación original ya que estamos trabajando sobre los mismos datos.
>MONTAR NO ES IGUAL A COPIAR

### Caso de uso del comando
Somos administradores de un equipo Linux en una pequeña empresa. Un compañero de trabajo necesita recuperar unos archivos importantes que se encuentran almacenados en una memoria USB que acaba de conectar al servidor.
Al conectar la memoria, verificas que el sistema detecta un nuevo dispositivo de almacenamiento con una capacidad de 64GB, pero sus archivos todavía no están disponibles en el sistema.
Nuestra tarea es preparar el acceso a la memoria para que los usuarios puedan consultar los archivos desde el directorio.
```bash
/mnt/documentos
```

Una vez que la memoria este disponible, debemos crear un archivo de prueba llamado verificacion.txt con lo siguiente "La memoria fue montada correctamente"

#### Solución
```bash
cd /mnt
sudo mkdir documentos
lsblk
sudo mount /dev/sda1 /mnt/documentos
cd /mnt/documentos
echo "La memoria fue montada correctamente" > verificacion.txt
```

### Notas Relacionadas
[[comandos-linux]]
[[lsblk]]
[[df]]
[[umount]]
