Tipo: Nota permanente
Fecha: 2026-07-23
Referencias:
* Linux.pdf
Temas:  #Compresion #Archivos #Linux 
### El comando tar
Comando en linux que nos ayuda a empaquetar varios archivos dentro de uno solo.
### Uso del comando
Si queremos crear un archivo tar, podemos seguir la siguiente sintaxis:
```bash
tar -cvf archivo.tar archivo/directorio
```

En caso de que queramos ver el contenido de un archivo tar utilizamos la siguiente sintaxis
```bash
tar -tvf archivo.tar
```

En algunas ocasiones no queremos que se muestren todos los archivos, a veces solo queremos ver un archivo en especifico, en eso casos utilizamos la siguiente sintaxis
```bash
tar -xOf archivo.tar ruta
```

En muchas ocasiones vamos a recibir archivos .tar provenientes de Internet, por lo que normalmente vamos a intentar extraer su contenido.
```bash
tar -xvf archivo.tar
```

El comando tar también nos puede ayudar a crear archivos gzip, esto mediante la siguiente sintaxis.
```bash
tar -czvf /ruta/archivo.tgz /ruta/archivoOrigen
```


### Caso de uso del comando tar
>La empresa IT-Solutions desarrolla una aplicación web para distintos cliente. Antes de realizar una actualización importante del sistema, el administrador de servidores debe crear un respaldo completo del proyecto ubicado en /var/www/PortalVentas, ya que si ocurre un error durante el despliegue, sera necesario restaurar la versión anterior.
>Actualmente el proyecto esta compuesto por cientos de archivos distribuidos en múltiples carpetas. Copiarlos uno por uno seria un proceso lento, propenso a errores y difícil de transferir a otro servidor para almacenarlo como respaldo.
```bash
tar -czvf portalVentas.tgz /var/www/PortalVentas
```


### Notas Relacionadas
[[gzip]]
[[zip]]
[[comandos-linux]]

