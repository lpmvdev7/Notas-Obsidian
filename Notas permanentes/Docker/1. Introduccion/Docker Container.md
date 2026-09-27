Tipo: Nota permanente
Fecha: 2026-09-23
Referencias:
* 
Temas: #Contenedores #Docker 
### ¿Que es un contenedor docker?
Un contenedor docker se puede definir como una instancia en ejecución de una imagen, siendo las imágenes plantillas que construimos a partir de lo que se conoce como dockerfiles.

### Contenedor a partir de un dockerfile
Tenemos el siguiente dockerfile que construye una aplicación en pyhon muy sencilla.
```dockerfile
FROM python:3.12.14-alpine

WORKDIR /app

COPY . . 

ENTRYPOINT ["python3"]

CMD ["app.py"]

```

El siguiente comando construirá una imagen docker a partir de nuestro dockerfile
```bash
docker build -t imagen-python:latest .
```

Ejecutamos el contenedor
```bash
docker run --name=imagen-py imagen-python:latest 
```

### Contenedor a partir de una imagen de tercero
Crear un dockerfile, volverlo imagen y ejecutarlo como contenedor no es la única forma existente de trabajar con contenedores, de hecho podemos empezar a trabajar con ellos descargándolos directamente desde dockerhub o algún otro registro de contenedores.
```bash
# Nos traemos la imagen a nuestro equipo.
docker pull corentinth/it-tools:latest

# Esto ejecuta un contenedor en localhost:8000  
docker run -d -p 8080:80 --name tools-dev -it corentinth/it-tools
```
![[Pasted image 20260923104338.png]]

### Docker CLI para ejecutar contenedores
```bash
# La flag -d indica detach mode, es decir que el contenedor se ejecuta en segundo plano
docker container run -d nginx

# Ejecutar una imagen de docker asignandole una terminal interactiva.
docker run -it ubuntu

# Darle nombre a nuestro contenedor
docker run --name mi_app nginx

# Mapear los puertos 8080 en el host y 80 en el contenedor.
docker run -p 8080:80 nginx

# Montar un volumen o directorio del host dentro del contenedor
docker run -v /ruta/host:/ruta/contenedor nginx

docker run --mount type=bind, source=/ruta/host, target=/ruta/contenedor nginx

# Definir variables de entorno dentro del contenedor.
docker run -e MYSQL_ROOT_PASSWORD=123 mysql

docker run --env-file <archivo> <imagen>

# Eliminar un contenedor automaticamente cuando termine su ejecuccion
docker run --rm alpine echo "Hola"

# Limitar la memoria RAM que puede usar el contenedor
docker run -m 512m nginx

# Limitar los CPUs que puede usar el contenedor
docker run --cpus="1.5" ubuntu

# Reinicio automatico definiendo politicas de reinicio, no, on-failure, always, unless-stopped
docker run --restart unless-stopped nginx


# Comando unificado
docker run -d -p 8080:80 -v /datos:/usr/share/nginx/html --restart unless-stopped nginx

```

### Otros comandos de contenedores
```bash
# Crea un contenedor pero no lo ejecuta, recibe las mismas flags que docker run
docker container create <imagen>

# Listar contenedores
docker container ls
docker container ls -a
docker ps
docker ps -a

# Eliminar contenedores
docker container rm <container-name>

# Iniciar un contendor 
docker container start <container>

# Detener un contenedor
docker container stop <container>

# Reiniciar un contenedor 
docker container restart <container>

# Ver los lofs de un contenedor
docker container logs <container>

# Mostrar los procesos en ejecuccion de un contenedor
docker container top <container>
```


### Notas Relacionadas
[[Dockerhub]]
[[Docker Image]]
[[Dockerfile]]


