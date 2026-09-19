Tipo: Nota permanente
Fecha: 2026-09-15
Referencias:
* 
Temas: #Docker #Dockerfile 
### ¿Que es un DockerFile?
Un dockerfile es un archivo de texto plano que contiene varias lineas, en donde cada linea representa una instrucción que llevara a este archivo a convertirse en una imagen de docker, la cual posteriormente se convertirá en un contenedor.

Dentro de un dockerfile, un usuario puede llamar a una gran variedad de instrucciones.

| Instruccion | Descripcion                                                                                                                                              |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FROM        | Define la imagen base a partir de la cual se construye nuestra imagen.                                                                                   |
| ARG         | Define una variable que solo esta disponible durante la construcción de la imagen                                                                        |
| RUN         | Ejecución de comandos dentro de una imagen mientras esta se construye.                                                                                   |
| CMD         | Comando por defecto que se ejecuta cuando el contenedor arranca. Solo puedo ser un comando.                                                              |
| ENTRYPOINT  | Similar a CMD, con la particularidad de que no se puede sobrescribir tan fácilmente.                                                                     |
| COPY        | Copia archivos o carpetas desde nuestra maquina hacia la imagen.                                                                                         |
| ADD         | Función similar a copy pero puede descargar archivos desde una URL y descomprimir archivos automáticamente.                                              |
| ENV         | Nos ayuda a definir variables de entorno que estaran disponibles tanto en el build como en el tiempo de ejecucion del contenedor.                        |
| EXPOSE      | Documenta que puerto usa una aplicación dentro del contenedor.                                                                                           |
| VOLUME      | Crea un punto de montaje para almacenamiento persistente, indicando que ese directorio debe manejarse fuera del sistema de archivos.                     |
| WORKDIR     | Establece el directorio de trabajo dentro del contenedor.                                                                                                |
| USER        | Especifica con que usuario se ejecutaran las instrucciones siguientes, esta instrucción es una excelente practica de seguridad.                          |
| LABEL       | Añade metadatos a la imagen en forma de pares clave-valor.                                                                                               |
| HEALTHCHECK | Define como docker debe comprobar si el contenedor sigue sano, ejecutando un comando periodicamente.                                                     |
| STOPSIGNAL  | Define que señal del sistema se envía al proceso principal del contenedor para detenerlo.                                                                |
| SHELL       | Cambia la shell por defecto.                                                                                                                             |
| ONBUILD     | Define instrucciones que se ejecutaran mas tarde, cuando la imagen que hemos creado se use como base de otra imagen. Útil para crear imágenes plantilla. |
### Leyendo un dockerfile
A continuación en el siguiente dockerfile, dejo algunos comentarios que le ayudaran al pablo del futuro o a quien sea que este leyendo esto a comprender que hace cada paso de este archivo.
```dockerfile
# Especificamos la imagen base sobre la cual construiremos nuestra imagen.
FROM python:3.12-slim

# Colocamos dos etiquetas especificando al que mantiene el contendor y una descripcion de lo que hace el contenedor 
LABEL maintainer="dev@ejemplo.com"
LABEL description="Servidor web para practicar Dockerfiles"

# Pasamos como argumento al build la version de la aplicacion, aunque esto realmente no tiene efecto alguna en la app en si ya que no usamos esta variable en ningun lado.
ARG APP_VERSION=1.0

# Creamos una variable de entorno en nuestra imagen especificano la ruta de trabajo de nuestra aplicacion en el contenedor.
ENV APP_HOME=/app

# Creamos otra variable de entorno en nuestra imagen indcando el ambiente en el que se esta desplegando la app.
ENV APP_ENV=production

# Establecemos el directorio de trabajo del contenedor en /app
WORKDIR ${APP_HOME}

# Copiamos el archivo requirements.txt de nuestro directorio actual.
COPY requirements.txt .

# Instalamos las dependencias listadas en requirements.txt especificando que no queremos directorio de cache.
RUN pip install --no-cache-dir -r requirements.txt

# Copiamos el proyecto al contenedor.
COPY . .

# Creamos un usuario llamado appuser, asignandole un home
RUN useradd --create-home appuser

# Colocamos a appuser como usuario y grupo propietario de /app
RUN chown -R appuser:appuser ${APP_HOME}

# A partir de ahora el proceso que ejecute el contenedor sera por parte del usuario appuser
USER appuser

# Documentamos que la aplicacion dentro del contenedor esta diseñada para escuchar en el puerto 8080. Expose sirve solo para documentar.
EXPOSE 8080

# Ejecutamos cada 30 segundos una peticion HTTP al endpoint /health. Si la peticion falla o genera un excepcion, el comando termina con codigo distinto a cero y Docker marca el contenedor como unhealthy
HEALTHCHECK --interval=30s --timeout=5s \
    CMD python -c "import urllib.request; urllib.request.urlopen('http://localhost:8080/health')" || exit 1

# Establecemos python como el ejecutable principal del contenedor. Los argumentos definidos en CMD se añadiran a este ejecutable.
ENTRYPOINT ["python"]

# Establecemos app.py como el argumento por defecto que se le pasa a python, juntandolos seria python app.py, ejecutando de esta manera la aplicacion.
# app.py puede ser cambiado por el usuario al ejecutar el contenedro, este puede colocar server.py o cualquier otro script que se encuentre dentro del proyecto.
CMD ["app.py"]
```

### Creando nuestros propios dockerfile

#### Dockerfile para nginx
```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

#### Dockerfile que ejecuta un script.
Creando un dockerfile que:
* Utilice Ubuntu 24.04
* Cree /app como directorio de trabajo
* Copie script.sh dentro del contenedor
* Le de permisos de ejecuccion
* Al iniciar el contenedor, ejecute script.sh de forma automatica
```dockerfile
FROM ubuntu:24.04

WORKDIR /app

COPY script.sh .

RUN chmod +x script.sh

CMD ["./script.sh"]
```

#### Dockerfile para app hecha en python
Crea un dockerfile para la siguiente aplicacion hecha con python
```bash
python-app/
├── Dockerfile
├── requirements.txt
└── app.py
```
Los requisitos son los siguientes:
* Python 3.12
* Usar una imagen slim
* EL directorio de trabajo deber ser /app
* Instalar las dependencias de requirements.txt
* Copiar el codigo de la aplicación
* La aplicación se inicia ejecutando app.py
* La aplicación usa el puerto 8000

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt 

COPY . .

EXPOSE 8000

CMD ["python","app.py"]

```

#### Dockerfile que cambia el usuario
Modifica el dockerfile anterior en base a los siguientes requisitos:
* Crear un usuario llamado appuser
* La aplicacion debe pertenecer a appuser
* El contenedor no debe ejecutar Python como root
* El usuario utilizado para ejecutar la aplicacion deber ser appuser.
```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt 

COPY . .

EXPOSE 8000

RUN useradd --create-home appuser

RUN chown -R appuser:appuser /app

USER appuser

CMD ["python","app.py"]
```

### Notas Relacionadas
[[Ejercicios-dockerfiles]]
[[Docker Image]]


