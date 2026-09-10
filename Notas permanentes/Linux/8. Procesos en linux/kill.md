Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
El comando kill usualmente es utilizado para matar procesos, pero este no es el unico uso que tiene. El comando lo que hace es mandar señales a los procesos y estas señales se encargan de realizar cosas como detener o matar el proceso, entre muchas otras cosas.

### Uso del comando
Anteriormente mencione que el uso mas comun del comando es para matar procesos, esto lo hacemos mediante la señal 9, SIGKILL.
```bash
kill -9 PID
```

Si únicamente colocamos el comando kill seguido del PID, lo que sucederá es que por defecto se llamara a SIGTERM es decir a la señal 15.
```bash
kill PID
```

Si queremos ver todas las señales disponibles hacemos lo siguiente:
```bash
kill -l 
 1) SIGHUP	 2) SIGINT	 3) SIGQUIT	 4) SIGILL	 5) SIGTRAP
 2) SIGABRT	 7) SIGBUS	 8) SIGFPE	 9) SIGKILL	10) SIGUSR1
3) SIGSEGV	12) SIGUSR2	13) SIGPIPE	14) SIGALRM	15) SIGTERM
4) SIGSTKFLT	17) SIGCHLD	18) SIGCONT	19) SIGSTOP	20) SIGTSTP
5) SIGTTIN	22) SIGTTOU	23) SIGURG	24) SIGXCPU	25) SIGXFSZ
6) SIGVTALRM	27) SIGPROF	28) SIGWINCH	29) SIGIO	30) SIGPWR
7) SIGSYS	34) SIGRTMIN	35) SIGRTMIN+1	36) SIGRTMIN+2	37) SIGRTMIN+3
8) SIGRTMIN+4	39) SIGRTMIN+5	40) SIGRTMIN+6	41) SIGRTMIN+7	42) SIGRTMIN+8
9) SIGRTMIN+9	44) SIGRTMIN+10	45) SIGRTMIN+11	46) SIGRTMIN+12	47) SIGRTMIN+13
10) SIGRTMIN+14	49) SIGRTMIN+15	50) SIGRTMAX-14	51) SIGRTMAX-13	52) SIGRTMAX-12
11) SIGRTMAX-11	54) SIGRTMAX-10	55) SIGRTMAX-9	56) SIGRTMAX-8	57) SIGRTMAX-7
12) SIGRTMAX-6	59) SIGRTMAX-5	60) SIGRTMAX-4	61) SIGRTMAX-3	62) SIGRTMAX-2
13) SIGRTMAX-1	64) SIGRTMAX	
```

### Tabla de señales

| Señal         | Uso cotidiano                                             |
| ------------- | --------------------------------------------------------- |
| SIGINT - 2    | Interrumpir un programa, es CTRL + C                      |
| SIGTERM - 15  | Solicitar una terminación ordenada                        |
| SIGKILL - 9   | Forzar la terminacion inmediata                           |
| SIGSTOP - 19  | Pausar un proceso                                         |
| SIGCONT - 18  | Reanudar un proceso pausado                               |
| SIGHUP - 1    | Recargar configuracion o indicar desconexion del terminal |
| SIGTSTP -  20 | Suspender un proceso desde el teclado, es CTRL + Z        |
| SIGCHLD - 17  | Notificar a un proceso padre que un hijo cambio de estado |

### Caso de uso
Somos dueños de un e-commerce que vende productos para mascotas. El sitio web se encuentra alojado en:
```bash
/var/www/petcommerce
```

El servidor ejecuta un script que sincroniza automáticamente el catalogo de productos con un proveedor externo. Sin embargo, debido a un error en la conexión con la API, el proceso entra en un bucle infinito y comienza a consumir recursos del servidor.
Mientras el proceso continua ejecutándose:
* Los clientes siguen navegando por el sitio
* Se realizan compras y consultas de productos
* El proceso defectuoso no aporta ningún beneficio y podría degradar el rendimiento del servidor.

Identificamos el PID del proceso
```bash
ps aux | grep sincronizar_catalogo.sh
```

Terminamos el proceso
```bash
kill 4821
```

En caso de que el proceso no responda a la señal SIGTERM, lo matamos. Esta opción siempre debe ser la ultima ya que cuando esto se ejecuta el proceso no tiene oportunidad de liberar recursos ni guardar información antes de finalizar.
```bash
kill -9 4821
```

### Notas Relacionadas
[[comandos-linux]]
[[ps]]


