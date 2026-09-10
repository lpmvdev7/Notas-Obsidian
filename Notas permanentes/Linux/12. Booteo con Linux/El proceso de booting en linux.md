Tipo: Nota permanente
Fecha: 2026-08-10
Referencias:
* Linux.pdf
Temas: #Booteo #Linux 
### Proceso completo de booting en linux
1. BIOS/UEFI
	1. Presionamos el botón de encendido en nuestro computador
	2. Se ejecuta un POST (Power on Self test) para comprobar que los componentes de hardware están funcionando correctamente.
	3. Se inicializan los componentes de hardware esenciales.
	4. De acuerdo con el orden de booteo la BIOS/UEFI identifica aquellos dispositivos booteables.
	5. Se carga y ejecuta el bootloader, en nuestro caso es GRUB.
2. Bootloader (GRUB)
	1. Se nos muestra un menu para elegir nuestro sistema operativo.
	2. Seleccionamos nuestro sistema operativo, grub toma ese kernel desde el disco duro y lo carga en la memoria RAM
	3. GRUB le pasa parametros al kernel, estos parametros son instrucciones que grub le pasa al kernel como la ruta de root y la version del kernel de linux
	4. Al mismo tiempo GRUB carga initramfs/initrd en la RAM
3. Inicializacion del kernel
	1. El kernel de linux al venir en archivos comprimidos, para este momento se descomprime completamente en memoria RAM
	2. Se inicializa la CPU, la memoria RAM y los dispositivos 
	3. Se monta el sistema de archivos de root /
	4. Se hace presente systemd ejecutando el proceso con PID 1 init.
4. Init System
	1. Se inicializan los otros procesos del sistema como systemd (servicios)

![](https://assets.bytebytego.com/diagrams/0213-linux-boot-process-explained.png)

![](https://pendrivelinux.com/wp-content/uploads/pendrivelinux-600x600.webp)

### Notas Relacionadas
[[BIOS]]
[[UEFI]]
[[GRUB]]
[[systemd]]
[[dmesg]]
