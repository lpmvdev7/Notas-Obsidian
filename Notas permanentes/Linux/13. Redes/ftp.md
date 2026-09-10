Tipo: Nota permanente
Fecha: 2026-08-12
Referencias:
* Linux.pdf
Temas: #Archivos #Transferencia-remota #Redes 
### ¿Que hace el comando?
El comando ftp en linux nos ayuda a interactuar con el protocolo de transferencia de archivos (FTP), es un comando que se utiliza para transferir archivos de un servidor a otro.

El comando ftp no viene instalado por defecto, al menos en la distribucion linux que uso al momento de escribir esta nota, para instalarlo usamos el siguiente comando:
```bash
# Instalacion del servidor virtual ftpd en distribuciones Debian, Ubuntu y Linux Mint
sudo apt install vsftpd

# Instalacion del comando ftp
sudo apt install ftp
```

Verificamos que el daemon del servicio se encuentre activo.
```bash
# Verificar el estado del daemon del servicio
sudo systemctl status vsftpd
```

### ¿Como funciona el comando?
El comando funciona colocando como parámetro la dirección ip de la maquina remota que contiene los archivos que queremos transferir.
```bash
ftp 172.18.0.2
```

Si lo hicmos bien, entramos al servidor remoto mediante una interfaz ftp.
```bash
# Con esto mostramos todos los comandos ftp disponibles
?
```

Estos son algunos de los comandos que se nos mostraran

| Comando | Uso                                                                             |
| ------- | ------------------------------------------------------------------------------- |
| cd      | Cambiar de directorio en la maquina remota                                      |
| lcd     | Cambiar de directorio en la maquina local                                       |
| ls      | Listar los nombres de los archivos y directorios en el directorio remoto actual |
| mkdir   | Crear una carpeta en el directorio remoto actual                                |
| pwd     | Imprimir la ruta actual en la maquina remota                                    |
| delete  | Eliminar un archivo en la maquina remota                                        |
| rmdir   | Eliminar un directorio en la maquina remota                                     |
| get     | Copiar un archivo de la maquina remota a la maquina local                       |
| mget    | Copiar multiples archivos de la maquina remota a la maquina local               |
| put     | Copiar un archivo de la maquina local a la maquina remota                       |
| mput    | Copiar multiples archivos de la maquina local a la maquina remota.              |

#### Ejemplos de uso de ftp
Queremos descargar un archivo usando ftp, ya estamos dentro del servidor remoto, ese archivo lo queremos en la carpeta Descargas de nuestro computador, que podemos hacer.
```bash
# Todos los comandos de aqui, fueron ejecutados dentro de un servidor ftp

# Imprimimos la ruta en la que nos encontramos en el servidor remoto
pwd

# Imprimimos la ruta en la que nos encontramos en nuesta maquina
!pwd

# Nos movemos a la carpeta Descargas 
lcd Descargas/

# Copiamos el archivo de la maquina remota a la local en la carpeta Descargas
get archivo.txt
```

### Notas Relacionadas
[[comandos-linux]]
[[rsync]]
[[scp]]

