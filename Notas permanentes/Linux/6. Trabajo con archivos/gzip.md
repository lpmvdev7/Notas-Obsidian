Tipo: Nota permanente
Fecha: 2026-07-24
Referencias:
* Linux.pdf
Temas: #Archivos #Compresion #Linux 
### El comando gzip
El comando gzip nos ayuda a comprimir archivos al formato open source gnu zip.

### Uso del comando
El comando puede ser utilizado para comprimir archivos, en esos casos utilizaremos la siguiente sintaxis
```bash
gzip archivo
```

También podemos utilizarlo para descomprimir un archivo
```bash
gzip -d archivo.gz
```

En algunas ocasiones necesitaremos conservar el archivo original, para esos casos podemos ejecutar lo siguiente:
```bash
gzip -k archivo
```

Si queremos ver la información de un archivo comprimido podemos usar la siguiente sintaxis.
```bash
gzip -l archivo.gz
```

### Caso de uso
La empresa IT-Solutions cuenta con un servidor web donde se aloja el portal de ventas de sus clientes. Todos los días el servidor genera archivos de registro (logs) que almacenan información sobre las peticiones HTTP, errores y accesos de los usuarios.
Después de varios meses, algunos archivos de registro alcanzan varios gigabytes de tamaño. Aunque estos logs ya no se utilizan diariamente, la empresa debe conservarlos durante un año por motivos de auditoria y para investigar posibles incidentes de seguridad.
El problema es que estos archivos consumen una gran cantidad de espacio en disco, lo que podría afectar el funcionamiento del servidor.

### Solución
```bash
gzip /var/log/web.log
```

### Notas Relacionadas
[[tar]]
[[zip]]
[[comandos-linux]]

