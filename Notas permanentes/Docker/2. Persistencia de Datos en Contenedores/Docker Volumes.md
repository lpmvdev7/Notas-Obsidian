Tipo: Nota permanente
Fecha: 2026-09-24
Referencias:
* https://docs.docker.com/engine/storage/volumes/
Temas: #Docker-volumes
### ¿Que son los volumenes en Docker?
Los volúmenes en docker son pequeños almacenes de datos administrados por docker, nos ayudan a tener persistencia de datos en nuestras aplicaciones.
Los volúmenes resuelven un problema muy importante a la hora de trabajar con docker, dado que los contenedores en docker están pensados para ser reemplazables debido al flujo de desarrollo moderno, los volúmenes tienen mucho sentido ya que tomamos la única parte de ese ciclo que no puede morir con el contenedor, los datos.
![](https://codigoelectronica.com/b/oscardevops/images/2020/06/base-ciclo-vida-contenedor-docker.jpg)

### Tipos de almacenamiento persistente en Docker
##### 1. Volúmenes gestionados por docker
Volúmenes docker completamente gestionados, estos se pueden compartir entre varios contenedores.
Los volúmenes gestionados por docker se guardan en:
```bash
/var/lib/docker/volumes/
```

Dependiendo de como ejecutemos nuestro volumen se guardara un hash o un nombre de volumen, siendo el hash un volumen anónimo y el nombre pues un named volume.

##### 2. Bind mounts
En este tipo de volumen es apuntas directamente a una carpeta de la maquina host. Son muy útiles en desarrollo

### Docker CLI para volúmenes
```bash
# Listar nuestros volumenes
docker volume ls 

# Crear un volumen nombrado, gestionado por docker
docker volume create api-data

# Crear un volumen anonimo, gestionado por docker, no recomiendo usar este comando a menos que sea con un nombre, como el ejemplo de arriba.
docker volume create

# Eliminar un volumen
docker volume rn <nombre/hash>

# Usando un named volume en un contenedor 
docker run -d -p 8080:80 --name=api -v api-data:/app/app-data api:latest

# Creando un volumen anonimo desde docker run
docker run -d -p 8080:80 --name=api -v /app/app-data api:latest

# Ejemplo de un bind mount 
mkdir -p /home/pablo/mis-datos
docker run -ti --name=linux-os -v /home/pablo/mis-datos:/datos debian:latest

# Inspeccionar un volumen
docker inspect data

# Montaje mas explicito de un volumen manejado por docker
docker run -d \
	--name=api
	--mount type=volume,source=api-data,target=/app/app-data \
	api:latest
	
# Montaje mas explicito de un volumen tipo bind
docker run -d \
	--name=api
	--mount type=bind,source=/home/pablo/mis-datos,target=/datos \
	debian:latest
```

### Caso de uso de un docker volume


### Notas Relacionadas



