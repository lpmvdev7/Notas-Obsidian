Tipo: Nota permanente
Fecha: 2026-08-10
Referencias:
* Linux.pdf
Temas: #Redes #Linux #Comandos 
### ¿Que hace el comando?
netstat es un comando que nos muestra información relacionada a los puertos que se encuentran conectados en nuestra computadora y en general estadísticas relacionadas a temas de red en linux.

### Uso del comando
El comando nos permite ver todas las conexiones TCP activas en nuestro computador
```bash
netstat 
Conexiones activas de Internet (servidores w/o)
Proto  Recib Enviad Dirección local         Dirección remota       Estado      
tcp        0      0 lpmvdev7linux:49302     ql-in-f188.1e100.n:5228 ESTABLECIDO
```

El comando también nos permite ver los puertos del computador
```bash
netstat -a 
Conexiones activas de Internet (servidores y establecidos)
Proto  Recib Enviad Dirección local         Dirección remota       Estado      
tcp        0      0 localhost:27124         0.0.0.0:*               ESCUCHAR   
tcp        0      0 0.0.0.0:ssh             0.0.0.0:*               ESCUCHAR   
tcp        0      0 0.0.0.0:http            0.0.0.0:*               ESCUCHAR   
```

Encontrar todos los puertos en escucha
```bash
netstat -l
```

Encontrar los puertos TCP en escucha
```bash
netstat -lt
```

Encontrar los puertos UDP en escucha
```bash
netstat -lu
```

Obtener un resumen de las conexiones en el computador.
```bash
netstat -s
```

Mostrar las interfaces de red
```bash
netstat -i
```

También es un comando que nos ayuda a realizar un constante monitoreo de la red.
```bash
netstat -c
```

Encontrar un proceso asociado
```bash
netstat -p
```

### Casos de uso
Somos administradores de un servidor linux donde recientemente se ha desplegado una aplicación web. Un compañero nos informa que no puede conectarse al servicio desde otro equipo de la red. 
Nosotros sabemos que la aplicación debería estar escuchando en el puerto TCP 8080, pero no sabemos si realmente esta escuchando, en que dirección esta enlazada y que otros puertos están abiertos actualmente.
Nuestro objetivo es investigar el estado de la conexiones y puertos del servidor usando netstat y de esa manera determinar que esta ocurriendo.

```bash
# Muetsrame todas las conexiones tcp activas y el PID asociado
netstat -ltnp
```

### Notas Relacionadas
[[comandos-linux]]
[[Comando ip]]
[[tcp]]
[[nmcli]]