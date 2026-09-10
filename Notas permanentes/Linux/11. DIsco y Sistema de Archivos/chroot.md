Tipo: Nota permanente
Fecha: 2026-08-07
Referencias:
* https://www.youtube.com/watch?v=GbbzllDqTQ4
Temas: #Almacenamiento #filesystem #Linux 
### ¿Que hace el comando?
Change root es un comando que cambia el directorio raíz actual hacia otro, es muy usado cuando montamos una partición y queremos cambiar el directorio raíz actual.
El comando encierra un programa dentro de un subdirectorio especifico, haciéndole creer al programa que ese subdirectorio es la raíz del sistema de archivos.

>chroot hace que un proceso vea un directorio determinado como si fuera /

### Sintaxis del comando
```bash
sudo chroot /mnt/new-linux
```

Salir de un entorno chroot
```bash
exit
```

### Caso de uso
Iniciamos Linux Mint desde un Live USB porque el sistema instalado en /dev/sda2 no arranca correctamente. Necesitamos acceder a la instalación ubicada en /dev/sda2 mediante chroot para poder repararla. Una vez terminado, debemos salir del entorno y desmontar la partición.
```bash
sudo mkdir -p /mnt/mint-recovery
sudo mount /dev/sda2 /mnt/mint-recovery
chroot /mnt/mint-recovery
# Comando que ayuda a reparar la instalacion, no lo conozco
# exit
sudo umount /mnt/mint-recovery
```

### Notas Relacionadas
[[comandos-linux]]
[[mount]]
[[umount]]


