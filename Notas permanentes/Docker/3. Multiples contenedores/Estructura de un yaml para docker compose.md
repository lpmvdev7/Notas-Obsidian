Tipo: Nota permanente
Fecha: 2026-10-02
Referencias:
* 
Temas: #docker-compose 
### Estructurar un yaml
En esta nota estaremos explorando como estructurar un archivo compose.yml o docker-compose.yml, para ello estaremos viendo la sintaxis de este tipo de archivos.

### Ejercicios de docker compose yml
Considero que la mejor manera de aprender algo es mediante la practica es por esa razón que estaré resolviendo algunos ejercicios relacionados a la creacion de archivos compose.yml

#### Ejercicio 1
Crear un archivo compose.yml que levante un contenedor utilizando la imagen ubuntu:latest, el contenedor debe llamarse ubuntu-test.
```yml
services:
  ubuntu-test:
    image: 'ubuntu:latest'
    container_name: ubuntu-test
    tty: true
    stdin_open: true
```

#### Ejercicio 2
Crea un servicio llamado python que utilice la imagen python:3.12-slim, el contenedor se llama python-container.
```yaml
services:
  python:
    image: 'python:3.12-slim'
    container_name: python-container
```

#### Ejercicio 3
Crea los siguientes tres servicios:
```
1. ubuntu
2. python
3. nginx
```
Estos servicios utilizan las siguientes imágenes respectivamente.
```bash
ubuntu:latest
python:3.12-slim
nginx:latest
```

```yml
services:
  ubuntu:
    image: 'ubuntu:latest'
  python:
    image: 'python:3.12-slim'
  nginx:
    image: 'nginx:latest'
```

#### Ejercicio 4
Crea un contenedor nginx que sea accesible desde localhost:3000, internamente dentro del contenedor utiliza el puerto 80.
```bash
services:
  servidor-nginx:
    image: 'nginx:latest'
    ports:
      - '3000:80'
    container_name: servidor-nginx
```

#### Ejercicio 5
Crea un contenedor usando la imagen latest de ubuntu y coloca dos variables de entorno APP_ENV y APP_VERSION, asignándoles los valores que quieras.

```bash
services:
  ubuntu-env:
    image: 'ubuntu:latest'
    environment:
      - APP_ENV=production
      - APP_VERSION=1.0
    tty: true
    stdin_open: true
    container_name: ubuntu-env
```

#### Ejercicio 6
Crea un archivo compose yml en el cual se usen variables de entorno de forma segura, mediante un archivo .env.
```bash
services:
  ubuntu-environment-machine:
    container_name: ubuntu-env-machine
    image: 'ubuntu:latest'
    env_file:
      - '.environment'
    stdin_open: true
    tty: true
```

#### Ejercicio 7 - Montaje de volúmenes
```yaml
services:
  ubuntu-mount:
    image: 'ubuntu:latest'
    container_name: 'ubuntu-mount'
    volumes:
      - './carpeta_montable:/container/carpeta_montable'
    stdin_open: true
    tty: true
```

#### Ejercicio 8 - Named volumes
Utilizando la imagen 16 de postgres crea un named volume llamado postgres-data.
```yml
services:
  postgres-services:
    image: 'postgres:16'
    container_name: postgres-services
    volumes:
      - 'postgres-data:/app'
    environment:
      - POSTGRES_PASSWORD=1234
volumes:
  postgres-data:
```

#### Ejercicio 9 - Ejecucion de comandos
Los archivos compose.yml, nos permiten ejecutar comandos al iniciar nuestros contenedores, esto lo hace dado una característica que modifica la linea CMD por defecto de nuestras imágenes.
```yml
services:
  ubuntu-comando:
    container_name: ubuntu-comando
    image: 'ubuntu:latest'
    command: echo "Hola Docker compose"

```
Esta característica nos puede ser muy útil en futuros proyectos.

#### Ejercicio 10 - Montando directorios de trabajo
```bash
services:
  ubuntu_workdir:
    container_name: ubuntu_workdir
    image: 'ubuntu:latest'
    working_dir: /app
    volumes:
      - './proyecto:/app'
    stdin_open: true
    tty: true
```

### Notas Relacionadas
[[Problemática con docker compose]]
[[docker run vs docker compose]]
[[docker-compose cli]]
