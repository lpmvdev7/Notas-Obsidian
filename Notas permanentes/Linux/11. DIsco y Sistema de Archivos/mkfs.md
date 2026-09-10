Tipo: Nota permanente
Fecha: 2026-08-07
Referencias:
* https://www.geeksforgeeks.org/linux-unix/mkfs-command-in-linux-with-examples/ 
Temas: #filesystem #Linux  
### ¿Que hace el comando?
El comando significa make filesystem, esta comando actúa sobre particiones de disco o dispositivos de almacenamiento, su función es asignar un sistema de archivo a estos dispositivos, preparando de esta manera a los dispositivos para guardar archivos.
>Este comando hay que usarlo con MUCHO CUIDADO ya que puede ejecutar acciones destructivas como borrar nuestros archivos y directorios en dispositivos de almacenamiento que si tienen datos.

### Sintaxis del comando
```bash
sudo mkfs.ext4 /dev/dispositivo
```

### Caso de uso 
Acabamos de conectar una memoria USB de 8GB a la computadora, nuestro objetivo es preparar la USB como almacenamiento en linux ya esta no tiene particiones, no tiene sistema de archivos y no puede guardar archivos.
```bash
sudo fdisk /dev/sdb
# Opciones dentro del menu interactivo de fdisk
# n
# 1
# +4GB
# w
sudo mkfs.ext4 /dev/sdb1
sudo mkdir -p /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
```
### Notas Relacionadas
[[comandos-linux]]
[[Tipos de sistemas de archivos]]

