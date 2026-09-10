Tipo: Nota permanente
Fecha: 2026-08-13
Referencias:
* https://www.youtube.com/watch?v=t18-C6f9y5Q
* Linux.pdf
Temas: 
### ¿Que hace el comando rsync?
El comando rsync es un comando que nos ayuda a copiar archivos, con el comando podemos copiar archivos entre directorios de nuestra misma maquina o incluso podemos copiar archivos entre diferentes computadores.

```bash
# Copia de archivos en entorno local
rsync [opciones] origen destino

# Copia de archivos de un entorno local a un entorno remoto
rsync [opciones] origen usuario@servidor:destino

# Copia de archivos de un entorno remoto a un entorno local
rsync [opciones] usuario@servidor:origen destino
```

### Casos de uso del comando
Podemos utilizar el comando cuando queremos copiar archivos de un directorio a otro, como lo haríamos con comandos como cp.
```bash
rsync archivo.txt ~/Escritorio/archivito.txt
```

También nos ayuda a copiar directorios completos a otras rutas
```bash
rsync -r ORIGEN/ DESTINO/
```

El caso de uso mas fascinante de rsync viene cuando hablamos de los metadatos de los archivos, es decir los permisos, la fecha de modificación y todos esos datos que vienen junto con los archivos, rsync nos permite copiar todo eso y dejarlo intacto en el destino.
```bash
# Con la opcion -a preservamos los metadatos de los archivos
rsync -ra ORIGEN/ DESTINO/
```

```bash
# Con la opcion -v imprimimos en stdout informacion de la operacion que estamos realizando.
rsync -rav ORIGEN/ DESTINO/
sending incremental file list
origen_1.txt

sent 221 bytes  received 35 bytes  512.00 bytes/sec
total size is 75  speedup is 0.29

```

El comando también nos permite mandar archivos desde nuestra computadora hasta una computadora remota.
```bash
rsync -rav ORIGEN/ luis@172.18.0.3:~/DESTINO
```

Con el comando también podemos excluir ciertos directorios o archivos que contienen datos que no queremos que se copien a otro lugar, para ello tenemos dos formas.
```bash
# Excluimos unicamente un archivo
rsync -ra --exclude=archivo.txt ORIGEN/ luis@172.18.0.3:~/DESTINO

# Excluimos los directorios listados en un archivo
echo "ignoredir/" > ORIGEN/ignore.txt
rsync -ra --exclude-from="ORIGEN/ignore.txt" ORIGEN/ luis@172.18.0.3:~/DESTINO

```

#### Ejemplo del comando en la vida real
Trabajas como administrador de sistemas para una pequeña empresa.
La empresa tiene un servidor linux con los archivos de su aplicacion web:
```bash
/var/www/miempresa/
├── uploads/
├── documentos/
├── reportes/
└── facturas/
```

Este directorio ocupa aproximadamente 35 GB
La empresa acaba de instalar un segundo servidor exclusivamente para respaldos:
```bash
Servidor principal: 192.168.1.10
Servidor de respaldo: 192.168.1.20
```

El jefe nos pide configurar un respaldo manual que podamos ejecutar cada noche.
* Los archivos deben copiarse desde servidor principal al servidor de respaldo
* No debes copiar nuevamente los archivos que no hayan cambiado
* Si un archivo fue modificado en el servidor principal, el respaldo debe actualizarlo.
* Si aparece un archivo nuevo, debe copiarse al respaldo.
* Si un archivo fue eliminado el servidor principal, también debe eliminarse del respaldo
* La transferencia debe realizarse mediante SSH
* Debes utilizar rsync para realizar la operación

```bash
# Solucion
rsync -rav --delete /var/www/miempresa usuario@192.168.1.20:/var/backups/mi-empresa-bkp
```
### Notas Relacionadas
[[comandos-linux]]
[[scp]]
[[ftp]]
[[secure shell]]
[[ssh]]
