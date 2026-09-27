Tipo: Nota permanente
Fecha: 2026-09-21
Referencias:
* 
Temas: #Docker #Registro-contenedores
### ¿Que es dockerhub?
Dockerhub es un registro de contenedores, los registros de contenedores son repositorios que contienen imágenes para que desarrolladores o equipos de TI puedan consumir.
Estos registros alojan miles de imágenes creadas por desarrolladores de todo el mundo lo que lo vuelve una plataforma de distribución de software para aquellos que usen docker.
![](https://www.docker.com/app/uploads/2024/10/1300x1300_generic-hub-blog_c-2.png)

### ¿Que papel juegan los registros de contenedores en el desarrollo moderno?
Los registros de contenedores juegan un papel fundamental en la metodología DevOps a continuación explicare el porque, para ello tomare como ejemplo una API hecha en python y explicare un proceso CI/CD básico desde cero.
1. Hacemos un git push de nuestro código hacia un servidor de hosting de código como Github, Gitlab, Gitea o Forgejo.
2. En estas plataformas configuramos un pipeline que se activa cada vez que se detecta un push.
3. Cuando el push se detecta se ejecuta una serie de tests para probar la integración del código a la rama principal.
4. Se integra el código a la rama main.
5. Se procede a crear una imagen de docker, para ello se ejecuta un build del dockerfile, en este build colocamos el hash del commit como tag de la imagen, esto nos permitirá controlar las versiones de todas nuestras imágenes.
6. Una vez creada nuestra imagen hacemos push de esta hacia un registro de contenedores como dockerhub, ECR o algun servidor dedicado que hayamos configurado con ese fin.
7. El siguiente paso dentro de nuestro pipeline es mandar al servidor de producción nuestra nueva imagen, para ello una forma que se me ocurre es conectarnos por SSH al servidor de producción, ejecutar un pull para después ejecutar la imagen con docker run y de esta manera desplegar nuestra aplicación en un entorno productivo.

Una vez hemos pasado por cada paso de la explicación nos podemos dar cuenta que los registros de imágenes juegan un papel fundamental en el despliegue de aplicaciones modernas, sobretodo en entornos cloud, esto es porque constituyen un paso fundamental para pasar las imágenes oficiales de nuestras aplicaciones a contenedores productivos en ambientes de producción. Ademas de que nos ofrecen la ventaja de funcionar como un historial el cual consultar en busca de una versión especifica de nuestra aplicación.

### Uso de Dockerhub con la CLI de docker
```bash
# Iniciar sesion con dockerhub
docker login

# Iniciar sesion en un registro privado
docker login <registro>

# Especificaf el usuario con el que se iniciara sesion en el registro
docker login -u <usuario>

# Cerrar sesion en dockerhub
docker logout

# Cerrar sesion en un registro en especifico
docker logout <registro>

# Descargar una imagen desde docker
docker image pull <imagen:tag>

# Descargar desde un registro distinto a dockerhub
docker pull <registro/imagen:tag>

# Subir imagenes a un registro
docker image push <usuario>/<imagen:tag>

# Subir imagenes a un registro privado
docker image push <registro>/<usuario><imagen:tag>

# Etiquetar imagenes
docker image tag <imagen_local> <usuario>/<imagen:tag>

docker image tag <imagen_local> <registro>/<usuario>/<imagen:tag>

# Buscar imagene en dockerhub
docker search <imagen>
```

### Comandos para registros privados
```bash
# Levantar un registro local
docker run -d -p 5000:5000 --name registro registry:2 

# Subir a un registro local
docker push localhost:5000/<imagen:tag> 

# Descargar desde el registro local
docker pull localhost:5000/<imagen:tag>
```

### Ejemplo con dockerhub
```bash
# Inicio sesion en dockerhub
docker login

# Creamos una aplicacion sencilla en python
cat app.py 
print("Hello world, mi nombre es pablo")

# Creamos un dockerfile
FROM python:3.12.14-alpine

WORKDIR /app

COPY . . 

ENTRYPOINT ["python3"]

CMD ["app.py"]

# Construimos nuestra imagen
docker build -t apppy:1.0 .

# Etiquetamos nuestra imagen colocando nuestro nombre de usuario, esto hara que se mande a un registro publico asociado a nuestro usuario en dockerhub
docker image tag apppy:1.0 lpmv024085/apppy:1.0

# Subimos nuestra imagen a un registro publico en dockerhub
docker push lpmv024085/apppy:1.0
```

### Ejemplo creando un registro privado.
Cuando queremos crear registros privados con docker, por lo general usamos la imagen llamada registry, esta imagen nos permite crear un contenedor que sirve como registro de imágenes docker local para nuestras aplicaciones.
```bash
# Crear y ejecutar el contenedor
docker run -d -p 5000:5000 --restart always --name registry registry:3

# Etiquetar las imagenes colocando el nombre del registro local
docker tag apppy:1.0 localhost:5000/app-python1.0

# Mandar las imagenes a nuestro registro local
docker push localhost:5000/app-python1.0:latest

# Hacemos un curl al siguiente endpoint y podemos ver que nuestra imagen se encuentra alli guardada.
curl -sX GET localhost:5000/v2/_catalog | jq
{
  "repositories": [
    "app-python1.0"
  ]
}
```

### Notas Relacionadas
[[Docker Image]]


