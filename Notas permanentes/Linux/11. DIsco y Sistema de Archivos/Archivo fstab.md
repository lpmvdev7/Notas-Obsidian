Tipo: Nota permanente
Fecha: 2026-08-07
Referencias:
* Linux.pdf
Temas: #Almacenamiento #Linux  
### ¿Que es el archivo fstab?
El archivo fstab ubicado en la ruta /etc/fstab es el archivo en el cual se declaran los discos del sistema, por lo general cuando utilizamos comandos como mount para montar sistemas de archivos en ciertas rutas del sistema, estos no prevalecen cuando reiniciamos el computador, es en estas situaciones que entra el archivo fstab, aquí declaramos nuestro punto de montaje y lo que pasara sera que cuando el sistema operativo cargue por completo nuestro montaje aparecerá en donde lo declaramos

```bash
cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=936ffd2d-9d35-4e1d-a82d-91490879ae9c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=60A0-5ADA  /boot/efi       vfat    umask=0077      0       1
```


Supongamos que tenemos un sistema de archivos en la particion /dev/sda5 y queremos montarla en /mnt/sda5, para que el montado de este sistema de archivos prevalezca el reinicio del computador, tenemos que declarar ese montaje en el archivo /etc/fstab siguiendo esta sintaxis
```bash
<fyle system> <mount point> <type> <options> <dump> <pass>
```
![[fstab-example.png]]

### Notas Relacionadas
[[fdisk]]
[[mount]]
[[mkfs]]

