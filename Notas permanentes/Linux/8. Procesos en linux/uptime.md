Tipo: Nota permanente
Fecha: 2026-08-01
Referencias:
* Linux.pdf
Temas: #Procesos #rendimiento
### ¿Que hace el comando?
El comando uptime se encarga de mostrarnos información sobre cuanto tiempo lleva encendido el sistema, que usuarios lo utilizan y la carga promedio del sistema. Es un comando que a mi consideración sirve para auditar el tiempo de consumo de una forma muy sencilla y simple

### Uso
Para utilizarlo solo tenemos que escribir lo siguiente en terminal:
```bash
uptime
```

El comando nos desplegara algo como esto
```bash
uptime
 14:22:29 up  1:18,  2 users,  load average: 0.21, 0.07, 0.01
```

### ¿Qué información nos brinda el comando?
* El comando nos informa cuanto tiempo lleva prendido el equipo, esto al decirnos la hora de arranque y el tiempo transcurrido.
* Los usuarios conectados al equipo
* El tiempo de carga promedio por minuto, últimos 5 minutos y últimos 15 minutos.

### Datos importantes de la carga promedio
El comando **uptime** entre muchos datos nos muestra la carga promedio en base al numero de cpus con los que cuenta nuestro equipo, para ver ese numero de cpus corremos el siguiente comando:
```bash
nproc
4
```

En este caso yo tengo 4 cpus, en base a ese numero puedo interpretar los resultados que me muestra el comando uptime con respecto a la carga promedio:
```bash
uptime
 14:22:29 up  1:18,  2 users,  load average: 0.21, 0.07, 0.01
```

* Carga promedio del ultimo minuto 0.21 > 4 =No
* Carga promedio de los últimos 5 minutos 0.07 > 4 = No 
* Carga promedio de los últimos 15 minutos 0.01 > 4 = No

Los resultados anteriores los podemos interpretar como que el CPU no se ha visto envuelto en una gran carga de trabajo dentro del ultimo lapso de 15 minutos ya que ni siquiera se llego a la mitad de su capacidad de procesamiento dentro de ese lapso.

### Casos de uso en la vida real
Supongamos que tenemos una empresa de software que quiere saber porque algunos de los procesos que tienen programados como automáticos tardan mucho en ejecutarse, un lugar para empezar a buscar seria el comando uptime, con este el administrador del sistema se podría dar cuenta de que la carga promedio esta superando a la capacidad de CPUs del equipo y por esa razón algunos procesos están en la cola de ejecución.

### Notas Relacionadas
[[comandos-linux]]
[[Tiempo de carga]]


