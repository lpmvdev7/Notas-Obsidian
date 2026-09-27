Tipo: Nota permanente
Fecha: 2026-09-21
Referencias:
* https://docs.docker.com/reference/cli/docker/
Temas: #Docker #Imagenes-docker
### ¿Que es una Imagen de Docker?
Podemos ver las imagines de docker como plantillas que contienen un conjunto de instrucciones. Esas instrucciones por si solas no hacen mucho, pero juntas y en el orden correcto crean contenedores de docker.

### ¿Como buscar imagenes?
Las imagenes se encuentran en lo que se conoce como registros de contenedores, estos registros son repositorios gigantescos en los cuales se encuentran varios imagenes docker, el mas famoso de este tipo es **dockerhub** aunque no es el único.
![[Pasted image 20260921182613.png]]

Otra forma de buscar imágenes docker es mediante el comando **docker search**, este comando escanea dockerhub en busca de la imagen que pasemos por parámetro.
```bash
docker search debian
NAME                DESCRIPTION                                     STARS     OFFICIAL
debian              Debian is a Linux distribution that's compos…   5319      [OK]
dockette/debian     My Debian Sid | Jessie | Wheezy Base Images     3         
gentkit/debian      A Docker image based on Debian Linux .          0         
corpusops/debian    debian corpusops baseimage                      0         
```

### Uso de Docker Images en la CLI
```bash
# Ver las imagenes que tenemos disponibles en nuestro equipo
docker image ls

# Traernos una imagen desde dockerhub
docker image pull ubuntu

# Inspeccionar una imagen
docker image inspect ubuntu

# Eliminar aquellas imagenes que no utilizamos
docker image prune

# Enviar una imagen a un registro
docker image pull ubuntu

# Eliminar una imagen
docker image rm ubuntu:latest

# Construir una imagen a partir de un dockerfile
docker image build -t python-app:1.0 .
```

### Notas Relacionadas
[[Dockerhub]]


