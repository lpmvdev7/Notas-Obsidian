Tipo: Nota permanente
Fecha: 2026-10-05
Referencias:
* 
Temas: #networking-docker 
### 1. Bridge
Dentro del host, docker crea una red privada interna.
```
ip a | grep "docker0"
```

### 2. Bridge definida por el usuario
Red de docker administrada por el usuario, el usuario la pueda crear mediante la linea de comandos de docker.
```bash
docker network create mi-red
```
Esta red tiene resolución DNS automática por nombre de contenedor y mejor aislamiento.

### 3. Host
Los contenedores que pertenecen a este tipo de red, comparten el mismo espacio de red que el host. Por lo que usar flags como -p, para hacer fordwarding de puertos entre el contenedor y el localhost ya no tiene sentido sino que directamente accedemos al puerto en nuestro computador.

```bash
# Esto ya no se hace
docker run --name="web-server" -p 80:80 nginx:latest

# Esto se hace
docker run --name="web-server" --network host nginx:latest
```

### 4. None
Los contenedores con el tipo de red none, no tienen ninguna red asociada, es decir que su única interfaz de red es loopback, su propio localhost. Este tipo de contenedores están completamente aislados de la red por lo que son usados para tareas muy muy especificas.
```bash
docker run --name="bbox" -ti --network none busybox
```

### 5. Macvlan
Los contenedores que pertenecen a redes de tipo macvlan reciben una dirección IP y MAC propia dentro de la red física a la que pertenece el host. Este tipo de redes en docker sirven cuando un contenedor necesita comportarse como un equipo físico mas de nuestra red.
* Software legacy que necesita conexión directa en la LAN
* Servidores de red: DNS, DHCP y similares
* Domotica y descubrimiento de dispositivos.

### 7. IPvlan
Los contenedores que pertenecen a redes de tipo IPvlan son aquellos que obtienen su propia dirección IP dentro de nuestra red, pero siguen teniendo la misma MAC del host.

### Notas Relacionadas
[[Redes Bridge en Docker]]
[[Redes Host en Docker]]
[[Redes None en Docker]]



