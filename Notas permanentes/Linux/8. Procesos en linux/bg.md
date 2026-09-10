Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
El comando bg se encarga de mover los procesos que se están ejecutando en primer plano a procesos que se ejecutan en segundo plano.
El caso de uso para este comando es el siguiente:
>Utiliza el comando bg cuando tengas muchas tareas en la terminal y necesites esta para seguir ejecutando comandos.

### ¿Como se usa el comando bg?
Pondremos a dormir 100 segundos a la terminal
```bash
sleep 100
```

Como podemos ver el proceso es bloqueante y no nos permite ejecutar mas comandos, para mandarlo a segundo plano lo primero que tenemos que hacer es **CTRL + Z** 
```bash
sleep 100
^Z
[1]+  Detenido                sleep 100
```

Tomamos el numero del job y se lo pasamos como argumento a **bg**
```bash
bg 1
```

De esta manera estaríamos logrando que el comando ejecutado desde un inicio pase de correr en primer plano a correr en segundo plano.
### Notas Relacionadas
[[comandos-linux]]
[[Procesos Background]]
[[Procesos Foreground]]
[[fg]]
[[jobs]]


