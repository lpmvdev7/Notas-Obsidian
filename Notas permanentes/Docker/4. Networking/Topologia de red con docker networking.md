Tipo: Nota permanente
Fecha: 2026-10-07
Referencias:
* 
Temas: #networking-docker 
### Topologia de red
A continuación recrearemos la siguiente topologia de red usando docker networking
![[topologia-red-docker-network.excalidraw|1000]]

### Archivo compose
Creamos un archivo compose.yml que representa la topologia mostrada en la imagen.
```yml
services:
  server1:
    container_name: server1
    image: 'busybox'
    stdin_open: true
    tty: true
    networks:
      - red1
    cap_add:
      - NET_ADMIN

  server2:
    container_name: server2
    image: 'busybox'
    stdin_open: true
    tty: true
    networks:
      - red1
    cap_add:
      - NET_ADMIN

  server3:
    container_name: server3
    image: 'busybox'
    stdin_open: true
    tty: true
    networks:
      - red2
    cap_add:
      - NET_ADMIN

  server4:
    container_name: server4
    image: 'busybox'
    stdin_open: true 
    tty: true
    networks: 
      - red2
    cap_add:
      - NET_ADMIN

  server5:
    container_name: server5
    image: 'busybox'
    stdin_open: true
    tty: true
    networks:
      - red1
      - red2
    cap_add:
      - NET_ADMIN

networks:
  red1:
    driver: bridge
  red2:
    driver: bridge
```

### Conociendo las otras redes
Dado el diseño de la topologia, existen dos redes, por cada red existen dos contenedores de docker que se pueden comunicar entre ellos mas no se pueden comunicar con los otros contenedores.
Teniendo esto en cuenta, existe un quinto contenedor que conoce a todos los demás.
Ahora que sabemos que existe un contenedor que conoce a todos, podemos usarlo como router para que los contenedores pertenecientes a redes diferentes se puedan conocer. Dentro del contenedor 5 ejecutamos el comando ip route para ver las redes a las que pertenece el contenedor 
```bash
# Server 5
ip route 
default via 172.19.0.1 dev eth1 
172.18.0.0/16 dev eth0 scope link  src 172.18.0.4 
172.19.0.0/16 dev eth1 scope link  src 172.19.0.4 
```

Para hacer que los contenedores de las diferentes redes se conozcan tenemos que modificar la tabla de ruteo de cada contenedor para que pase por el único contenedor que si conoce a todos.
```bash
# Server1
ip route add 172.18.0.0/16 via 172.19.0.4

# Server2
ip route add 172.18.0.0/16 via 172.19.0.4

# Server3
ip route add 172.19.0.0/16 via 172.18.0.4

# Server4
ip route add 172.19.0.0/16 via 172.18.0.4
```

De esta manera todas las redes se conocen entre si.

### Conclusión
Este ejercicio me hizo repasar varios temas que vi durante mi carrera en ingeniería en Software,  durante el desarrollo del ejercicio estuve aprendiendo a armar topologias de red usando docker y junto a ellos mis conocimientos en redes y en linux para poder hacer funcionar todo.
### Notas Relacionadas
[[Redes Bridge en Docker]]
[[Redes en docker]]
[[Comando ip]]
[[About - Redes]]
