Tipo: Nota permanente
Fecha: 2026-07-30
Referencias:
* Linux.pdf
Temas: #Procesamiento-texto #Archivos #Comandos 
### ¿Que es el comando awk?
awk es un comando que nos ayuda a procesar texto en linux, es ampliamente conocido por su capacidad de manipulación sobre archivos que muestran datos en columnas, véase estos como archivos csv, xlsx o archivos de configuración en linux.

Por ejemplo, si ejecutamos un comando como **ls -lh** podemos ver que el stdout nos muestra una serie de columnas.
```bash
pablo@lpmvdev7linux:~/Escritorio$ ls -lh 
total 28K
drwxrwxr-x  2 pablo pablo 4.0K may 14 12:56 Apuntes
drwxrwxr-x  3 pablo pablo 4.0K jul 21 16:44 Claude
drwxrwxr-x  4 pablo pablo 4.0K feb 20 10:41 Ensayos-Libros
drwxrwxr-x  5 pablo pablo 4.0K jul 24 14:05 Estudio
lrwxrwxrwx  1 pablo pablo   36 jul 24 14:05 link -> /home/pablo/Escritorio/Estudio/linux
drwxrwxr-x 10 pablo pablo 4.0K jun 12 11:47 practicas
drwxrwxr-x 16 pablo pablo 4.0K jul 22 13:43 Proyectos
drwxrwxr-x  3 pablo pablo 4.0K jun 12 12:23 Universidad
pablo@lpmvdev7linux:~/Escritorio$ 
```

Usando awk únicamente podemos imprimir los nombres de archivos y carpetas.
```bash
pablo@lpmvdev7linux:~/Escritorio$ ls -lh | awk '{print $9}'

Apuntes
Claude
Ensayos-Libros
Estudio
link
practicas
Proyectos
Universidad
```

### Como usar el comando
Como la gran mayoría de comandos en linux, awk nos da una gran variedad de opciones dependiendo de lo que queramos hacer con el.

Si queremos imprimir una columna en especifico tenemos la sintaxis mas básica del comando
```bash
awk '{print $numero_columna}' archivo.txt
```

Si queremos imprimir varias columnas de un archivo, únicamente agregamos el numero de esas columnas.
```bash
awk '{print $numero_columna $numero_columna}' archivo.txt
```

En ocasiones trabajaremos con archivos csv, los cuales tienen datos separados por coma, en estas ocasiones necesitaremos de la opción **-F**
```bash
awk -F 'delimitador' '{print $2}' archivo.csv
```

### Notas Relacionadas
[[comandos-linux]]
[[awk-condicionales]]
[[awk-variables]]



