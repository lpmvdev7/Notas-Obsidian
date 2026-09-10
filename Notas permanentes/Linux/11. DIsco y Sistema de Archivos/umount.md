Tipo: Nota permanente
Fecha: 2026-08-07
Referencias:
* Linux.pdf
* https://phoenixnap.com/kb/linux-mount-command
Temas: #Almacenamiento #filesystem 
### ¿Que hace el comando?
Comando que se encarga de desmontar sistemas de archivos haciendo que sean inaccesibles. 
>Este comando tiene que ser utilizado con mucho cuidado

### Sintaxis
```bash
umount /ruta
```

Supongamos que tenemos una usb montada en la siguiente ruta
```bash
/mnt/usbMounted
```

Usando el comando umount podemos desmontarla pasando como argumento la ruta al directorio montado.
```bash
umount /mnt/usbMounted
```

### Notas Relacionadas
[[comandos-linux]]
[[mount]]



