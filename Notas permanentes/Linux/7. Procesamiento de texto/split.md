Tipo: Nota permanente
Fecha: 2026-07-30
Referencias:
* Linux.pdf
Temas: #Procesamiento-texto #Archivos 
### ¿Para que sirve split?
Comando que sirve para dividir el contenido de archivos en partes mas pequeñas.

Supongamos que tengo un archivo con 100 correos, me gustaría dividir este archivo en uno mas pequeño.
```text
sofia245@outlook.com
patricia306@protonmail.com
claudia227@protonmail.com
carmen716@yahoo.com
monica182@gmail.com
ana465@protonmail.com
monica253@gmail.com
diego831@outlook.com
carlos170@gmail.com
mariana724@outlook.com
paola509@outlook.com
claudia443@protonmail.com
ximena385@protonmail.com
....
```

Suponiendo que lo queramos dividir en pequeños archivos de 10 lineas cada uno el comando que tendríamos que utilizar seria el siguiente:
```bash
split -l 10 mails.txt
```

Después de ejecutarlo el comando crea varios archivos que empiezan con x.
```bash
ls
mails.txt  xaa  xab  xac  xad  xae  xaf  xag  xah  xai  xaj
```

Incluso podemos dividir un archivo mediante la definición de su tamaño en bytes.
```bash
split -b 1k mails.txt 
```

```bash
ls -lh 
total 16K
-rw-rw-r-- 1 pablo pablo 2.2K jul 30 18:55 mails.txt
-rw-rw-r-- 1 pablo pablo 1.0K jul 30 19:04 xaa
-rw-rw-r-- 1 pablo pablo 1.0K jul 30 19:04 xab
-rw-rw-r-- 1 pablo pablo  154 jul 30 19:04 xac
```

### Notas Relacionadas
[[comandos-linux]]


