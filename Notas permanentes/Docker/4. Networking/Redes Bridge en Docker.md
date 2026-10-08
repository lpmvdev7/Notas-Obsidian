Tipo: Nota permanente
Fecha: 2026-10-05
Referencias:
* 
Temas: #networking-docker 
### Sobre las Redes Bridge en Docker
Las redes bridge en docker son aquellas que estaremos utilizando la mayor parte del tiempo cuando usemos docker, existen dos tipos, la primera es la red default de docker, la cual podemos ver ejecutando el siguiente comando:
```bash
# Veremos la interfaz de red de docker.
ip addr | grep "docker0"
```

La segunda son las redes que nosotros como usuarios podemos administrar y a mi consideración a las que les podemos sacar mas jugo.
```bash
# Nos muestra todas las redes de docker
docker network ls
```

### Ejercicios 

#### Ejercicio 1
Crear una DNS usando una bridge administrada por nosotros.
La red estará compuesta de dos contenedores linux.
```bash
# Creamos una red
docker network create lnx-ntw

# Creamos dos servidores
docker run -dit --name server1 busybox
docker run -dit --name server2 busybox

# Conectamos los contendores a la red
docker network connect lnx-ntw server1
docker network connect lnx-ntw server2
```

```bash
# Dentro de server1 hacemos ping hacia server2
docker exec -ti server1 sh

# Hacemos ping al server2
ping server2
PING server2 (172.18.0.3): 56 data bytes
64 bytes from 172.18.0.3: seq=0 ttl=64 time=0.108 ms
64 bytes from 172.18.0.3: seq=1 ttl=64 time=0.091 ms
64 bytes from 172.18.0.3: seq=2 ttl=64 time=0.150 ms
64 bytes from 172.18.0.3: seq=3 ttl=64 time=0.166 ms
64 bytes from 172.18.0.3: seq=4 ttl=64 time=0.106 ms

```

```bash
# Dentro de server2 hacemos ping hacia server2
docker exec -ti server2 sh

# Hacemos ping al server
ping server1
PING server1 (172.18.0.2): 56 data bytes
64 bytes from 172.18.0.2: seq=0 ttl=64 time=0.125 ms
64 bytes from 172.18.0.2: seq=1 ttl=64 time=0.108 ms
64 bytes from 172.18.0.2: seq=2 ttl=64 time=0.135 ms
64 bytes from 172.18.0.2: seq=3 ttl=64 time=0.124 ms
```

También podemos resolver este ejercicio usando docker compose.
```yml
services:
  server1:
    image: 'busybox'
    container_name: server1
    stdin_open: true
    tty: true
    networks:
      - servers_network

  server2:
    image: 'busybox'
    container_name: server2
    stdin_open: true
    tty: true
    networks:
      - servers_network

networks:
  servers_network:
    driver: bridge
```
#### Ejercicio 2
Crear dos redes aisladas y confirmar mediante el uso del comando ping que estas no se ven.
```yml
services:
  server1:
    image: 'busybox'
    container_name: server1
    tty: true
    stdin_open: true
    networks:
      - lnx-red1
  server2:
    image: 'busybox'
    container_name: server2
    tty: true
    stdin_open: true
    networks:
      - lnx-red1
  server3:
    image: 'busybox'
    container_name: server3
    tty: true
    stdin_open: true
    networks:
      - lnx-red2

networks:
  lnx-red1:
    driver: bridge
  lnx-red2:
    driver: bridge
```
En el archivo se define que los contenedores server1 y server2 pertenecen a la misma red (lnx-red1), mientras que el tercer contenedor pertenece a la red 2.
```bash
# Dentro de server2

# Hacemos ping a server1
ping -c 5 server1
PING server1 (172.19.0.2): 56 data bytes
64 bytes from 172.19.0.2: seq=0 ttl=64 time=0.121 ms
64 bytes from 172.19.0.2: seq=1 ttl=64 time=0.196 ms
64 bytes from 172.19.0.2: seq=2 ttl=64 time=0.206 ms
64 bytes from 172.19.0.2: seq=3 ttl=64 time=0.300 ms
64 bytes from 172.19.0.2: seq=4 ttl=64 time=0.201 ms

# Tratanos de hacer ping a server3 pero no funciona
ping server3
ping: bad address 'server3'
```

### Notas Relacionadas
[[Tipos de Redes en Docker]]
[[Topologia de red con docker networking]]

