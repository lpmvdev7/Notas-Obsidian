Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
Comando encargado de imprimir los procesos que se están ejecutando actualmente en el sistema, el comando lo que hace es un tipo screenshoot de los procesos en ejecución por lo que este no se actualiza en tiempo real

>El comando ps imprime información sobre los procesos en ejecución

### Como se usa el comando
El uso mas común del comando es mediante la siguiente sintaxis:
```bash
ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.1  23420 11072 ?        Ss   08:40   0:01 /sbin/init splash
```

El comando también puede ser utilizado para mostrar únicamente los datos que nos interesan.
```bash
ps -o pid,user,ppid,%cpu,%mem,cmd
```

O también para ver un proceso en especifico.
```bash
ps -p 9114
```

Por ultimo uno de los mas utilizados para ver los procesos del sistema.
```bash
ps -ef
```

### Notas Relacionadas
[[comandos-linux]]
[[top]]
[[htop]]


