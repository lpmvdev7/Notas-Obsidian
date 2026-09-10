Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf 
Temas: #Procesos 
### ¿Que hace el comando?
El comando fg se encarga de mover procesos que se encuentran en segundo plano a procesos que se ejecutan en primer plano.

### ¿Como se usa?
Como ejemplo de uso creare un proceso que pondrá en espera la terminal por 100 segundos y mandare ese proceso a segundo plano.
```bash
sleep 100&
[1] 8202
jobs
[1]+  Ejecutando              sleep 100 &
```

Utilizando el numero de jobs, aquel encerrado entre [], nos traemos este proceso a primer plano con el comando fg
```bash
fg 1
sleep 100
```

Una vez que nos traemos el proceso a primer plano, la terminal se bloqueara debido a que esta a la espera de que el comando termine de ejecutarse.
### Notas Relacionadas
[[comandos-linux]]
[[Procesos Foreground]]
[[Procesos Background]]
[[bg]]
[[jobs]]


