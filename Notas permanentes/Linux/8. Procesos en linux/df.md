Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
El comando nos muestra el uso del disco duro.
```bash
df
```

También nos ayuda a mostrarnos el sistema de archivos que tenemos montado en nuestro computador, en mi caso ext4
```bash
df -Th
S.ficheros     Tipo     Tamaño Usados  Disp Uso% Montado en
tmpfs          tmpfs      764M   2.7M  762M   1% /run
efivarfs       efivarfs   268K   149K  115K  57% /sys/firmware/efi/efivars
/dev/nvme0n1p5 ext4       192G    78G  105G  43% /
```

Podemos personalizar la salida del comando df, mediante la opción --output.
```bash
df --output='size','used','avail','pcent'
bloques de 1K   Usados      Disp Uso%
       782300     2684    779616   1%
          268      149       115  57%
    200474896 81036484 109182028  43%
      3911484    53220   3858264   2%
         5120       12      5108   1%
      3911484        0   3911484   0%
       262144    71120    191024  28%
       782296     3704    778592   1%

```
### Notas Relacionadas
[[free]]
[[Sistema de archivos]]
[[Tipos de sistemas de archivos]]


