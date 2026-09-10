Tipo: Nota permanente
Fecha: 2026-08-10
Referencias:
* Linux.pdf
Temas: #Linux #Redes #Comandos 
### ¿Que hace el comando?
El comando ip en linux es una utilidad de la linea de comandos que nos permite la administración básica de la red en nuestro computador.

### Uso del comando
El comando tiene varios usos para la administración de red.

Podemos usarlo para ver todas las interfaces de red en nuestro computador y de paso ver nuestra dirección ip.
```bash
# El comando nos mostrara todas las interfaces de red de nuestro sistema numeradas
# En mi caso son
# 1 lo (localhost)
# 2 enp43s0 (ethernet)
# 3 wlp0s20f3 (wifi)
# 4 docker0 (interfaz de red virtual de docker)
ip a
```

También podemos ver una interfaz de red en especifico dentro de nuestro sistema.
```bash
# Ver la informacion especifica de una interfaz de red
ip a show wlp0s20f3 
```

Ver las interfaces de red existentes
```bash
ip link
```

El comando también nos ayuda a levantar o tumbar una interfaz de red.
```bash
# Levantamos la interfaz de red de wifi
sudo ip link set wlp0s20f3 up

# Tumbamos la interfaz de red de wifi
sudo ip link set wlp0s20f3 down
```

El comando también sirve para agregar o borrar una dirección IP de una interfaz
```bash
# Agregar una direccion ip a una interfaz de red
sudo ip a add ip/mask dev interfaz

# Eliminar una direccion ip a una interfaz de red
sudo ip a del ip/mask dev interfaz

# Ejemplo de uso
sudo ip a add 192.168.1.1/24 dev wlp0s20f3
```

Mostrar la tabla de ruteo
```bash
# Mostrar la tabla de ruteo
ip r
```

### Caso de uso para el comando ip
Estas administrando un servidor linux que acaba de ser conectado a la red mediante un cable ethernet. Un compañero te informa que no puede acceder a los servicios internos de la empresa desde ese servidor.
Al revisar rápidamente el equipo, sabes que la interfaz Ethernet es enp43s0.
Tu objetivo es diagnosticar y corregir el problema utilizando únicamente el comando ip.
Al finalizar, el servidor deber poder comunicarse correctamente con la red interna.

```bash
# Solucion

# Veo la informacion resumida de las interfaces de red disponibles.
ip -br l

# Si la interfaz esta en estado DOWN la levanto con el siguiente comando
ip link set enp43s0 up

# Veo el default gateway (aquella ip mencionada en default via)
ip r

# Basado en el default gateway agrego una ip correspondiente a ese segmento
ip a add 192.168.1.50/24 dev enp43s0
```

### Notas Relacionadas
[[comandos-linux]]
[[Interfaces de red]]

