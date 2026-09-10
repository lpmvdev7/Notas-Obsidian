Tipo: Nota permanente
Fecha: 2026-07-24
Referencias:
* Linux.pdf 
Temas:  #Linux #Archivos #Copiado
### Que hace el comando cp
El comando cp sirve para copiar un archivo o un directorio a otro lugar en nuestro sistema de archivos linux.
Puede ser ampliamente utilizado en scripts por motivos de automatización de tareas.

### Uso de cp
Si queremos copiar un archivo a otra ubicación lo hacemos con la siguiente sintaxis:
```bash
cp ruta-origen/archivo.txt ruta-destino/destino.txt
```

Si queremos que el archivo mantenga su nombre al ser copiado en la otra ubicación, solo hacemos referencia al directorio en donde vivirá el archivo.
```bash
cp ruta-origen/archivo.txt ruta-destino/
```

Cuando queramos copiar un directorio tenemos que hacer uso de la opción -r.
```bash
cp -r ruta-directorio/ ruta-destino/
```

En algunas ocasiones, por motivos de visibilidad vamos a querer verificar que archivos de un directorio se están copiando, para ello tenemos la opción -v.
```bash
cp -vr ruta-directorio/ ruta-destino/
```

### Caso de uso del comando cp
>Trabajas como soporte técnico en una pequeña empresa. El administrador de la pagina web te pide ayuda antes de hacer una actualización riesgosa: quiere modificar el archivo de configuración config.php del sitio web, pero tiene miedo de romper algo y no tener como regresar a la versión que funcionaba.
>Te menciona: "Antes de tocar nada, necesito una copia de seguridad de ese archivo, y si algo sale mal, poder restaurarlo rápido."
>Ademas, te comenta que también quiere que le copies toda la carpeta sitio_web/ a una ubicación de respaldo sitio_web_backup, por si la actualización afecta mas de un archivo.

### Solución
Problemática 1: copiar el archivo config.php
```bash
cp config.php ~/Escritorio/backup/
```

Problemática 2: copiar la carpeta sitio_web/
```bash
cp -vr sitio_web/ ~/Escritorio/sitio_web_backup
```


### Notas Relacionadas
[[comandos-linux]]



