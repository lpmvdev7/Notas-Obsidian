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
En este tipo de volumenes apuntas directamente a una carpeta de la maquina host. Son muy útiles en desarrollo

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
Imaginemos el siguiente ejemplo, tenemos una carpeta en windows en la cual se generan diariamente facturas, como requisito organizacional necesitamos separar los archivos pdf en una carpeta diferente, esto para prepararlos para impresión.

**¿Como solucionarías esta problemática usando docker?**

Lo primero que haría seria crear un script en bash que ejecute la operación objetivo.
```bash
#! /bin/bash

# Validez de los argumentos pasados por script
validacion(){
	if [[ $# -eq 0 || $# -gt 1 ]];then
		return 1
	else
		# Comprobar que el argumento sea un directorio
		if [[ -d $1 ]];then
			return 0
		else
			return 1
		fi
	fi
}

# Crear una copia de la carpeta pasada como argumento
copiaCarpeta(){
	cp -r "${1%/}/" "${1%/}_copia/"
	return 0
}


# Navegar a la carpeta
navegarCarpeta(){
	cd "${1%/}_copia/"
}

# Borrar por extension de archivo
borrarExtension(){
	rm *."xml"
}


# Flujo del programa
implementacion(){
	usuario=$1
	validacion $usuario
	if [[ $? -eq 0 ]];then
		copiaCarpeta $usuario
		if [[ $? -eq 0 ]];then
			navegarCarpeta $usuario
			if [[ $? -eq 0 ]];then
				borrarExtension
				if [[ $? -eq 0 ]];then
					return 0
				else
					return 1
				fi
			else
				echo "Usage: $0 <dir>"
				return 1
			fi
		else
			echo "Usage: $0 <dir>"
			return 1
		fi

	elif [[ $? -eq 1 ]];then
		echo "Usage: $0 <dir>"
		return 1 
	fi
}

implementacion $1

```

Ahora creamos un dockerfile
```dockerfile
FROM ubuntu:latest

WORKDIR /container

COPY automatizacion_facturas.sh .

RUN chmod +x automatizacion_facturas.sh

CMD ["bash"] 
```

Construimos la imagen de nuestro proyecto.
```bash
# Nos aseguramos que en donde ejecutemos este comando se encuentre el dockerfile
docker build -t proyecto_volumen .
```

Dentro de la carpeta de nuestro proyecto creamos dos carpetas, la primera servirá como la carpeta en donde tendremos nuestras facturas y la otra como la carpeta en donde guardaremos el resultado de ejecutar nuestro script en el contenedor.
```bash
# Carpeta que contendra todas nuestras facturas
mkdir facturas
cd facturas
touch archivo{1..9}.xml
touch archivo{1..9}.pdf

# Carpeta que contendra el resultado
mkdir output
```

Ejecutamos el comando
```bash
docker run -ti --name="volumen1" -v /home/pablo/contenedores/proyecto_volumes/facturas:/container/facturas -v /home/pablo/contenedores/proyecto_volumes/output:/container/output proyecto_volumen:latest
```

Dentro del contenedor ejecutamos lo siguiente
```bash
# Ejecutamos el script colocando como argumento la carpeta facturas
bash automatizacion_facturas.sh facturas/

# Mandamos la nueva carpeta que se creo hacia la carpeta output
mv facturas_copia output
```

Al salirnos del contenedor y dirigirnos hacia nuestra maquina host podemos ver que la carpeta resultante únicamente con los pdf ya se encuentra disponible.
```bash
cd output
cd facturas_copia
ls
archivo1.pdf  archivo3.pdf  archivo5.pdf  archivo7.pdf  archivo9.pdf
archivo2.pdf  archivo4.pdf  archivo6.pdf  archivo8.pdf
```

Esto ya nos sirve para mantener un orden en nuestros archivos.

#### Dibujo de la solución
![[volume_container_exercise.excalidraw | 1000]]

### Notas Relacionadas
[[Bash Scripting]]
[[About - Persistencia de Datos en Contenedores]]
[[Montaje de Volumenes Docker]]


