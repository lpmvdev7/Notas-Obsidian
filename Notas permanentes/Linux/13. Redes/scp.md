Tipo: Nota permanente
Fecha: 2026-08-13
Referencias:
* Linux.pdf
Temas: #Transferencia-remota #Archivos #Redes 
### ¿Que hace el comando?
El comando significa secure copy, es un comando que nos permite copiar directorios y archivos de forma segura a través de la red usando el protocolo secure shell (SSH).
```bash
scp [opciones] origen destino
```

### Usos del comando scp
```bash
# Copiar un archivo a un servidor remoto
scp hello.txt pablo@192.168.1.100:/home/pablo/scp

# Copiar un archivo del servidor remoto a la maquina local
scp pablo@192.168.1.100:/home/pablo/scp/adios.txt /home/pablo/scp

# Copiar un directorio entero con el comando scp y ver los detalles
scp -rv /home/pablo/scplocal/ pablo@192.168.1.100:/home/pablo/scp

# Copiado de archivos entre hosts remotos (tenemos que tener acceso de red a esas maquinas, para que el comando funcione)
scp pablo@192.168.1.100:/home/pablo/file.txt pablo@192.168.1.104:/home/pablo

# Copiado de directorios entre hosts remotos
scp -r pablo@192.168.1.100:/home/ubuntu pablo@192.168.1.104:/home/pablo

# Comprimir los archivos al momento de copiarlos
scp -C mint.txt pablo@192.168.1.100:/home/pablo

# Preservar los metadatos orginales de los archivos copiados
scp -p mint.txt pablo@192.168.1.100:/home/pablo

# Tomar una identidad ssh para copiar un archivo a un host remoto
scp -i ~/.ssh/key.pem archivo.txt pablo@192.168.1.100:/home/pablo/
```

### Ejemplo de scp
Necesitamos copiar el archivo backup.sql  que se encuentra en tu computadora local hacia el directorio /home/usuario/backups/ de un servidor Linux con IP 192.168.1.20 utilizando SSH y el comando scp.
```bash
scp backup.sql pablo@192.168.1.20:/home/pablo/backups
```

### Notas Relacionadas
[[comandos-linux]]
[[ftp]]
[[rsync]]


