Tipo: Nota permanente
Fecha: 2026-08-01
Referencias:
* 
Temas: #Autenticacion 
### ¿Que hace el comando?
El comando last nos ayuda a verificar los usuarios que se han conectado al servidor. El comando funciona debido a que le el archivo wtmp que se encuentre en /var/log.

### Como se ejecuta el comando?
La sintaxis general de uso del comando es 
```bash
last
```

Nos mostrara algo como lo siguiente:
```bash
last
pueblo   pts/1        192.168.1.44     Sat Aug  1 16:05   still logged in
pueblo   tty7         :0               Sat Aug  1 14:50    gone - no logout
reboot   system boot  6.14.0-37-generi Sat Aug  1 14:49   still running
pueblo   pts/1        192.168.1.44     Sat Aug  1 14:22 - crash  (00:27)
pueblo   tty7         :0               Sat Aug  1 13:05 - crash  (01:44)
reboot   system boot  6.14.0-37-generi Sat Aug  1 13:04   still running
pueblo   tty7         :0               Sat Jul 25 12:07 - crash (7+00:57)
reboot   system boot  6.14.0-37-generi Sat Jul 25 12:05   still running
pueblo   pts/1        192.168.1.29     Sat Jan 10 11:48 - 13:52  (02:04)
pueblo   tty7         :0               Sat Jan 10 11:22 - 13:52  (02:30)
reboot   system boot  6.14.0-29-generi Sat Jan 10 11:21 - 13:52  (02:31)
pueblo   tty7         :0               Sat Jan 10 11:15 - crash  (00:05)
reboot   system boot  6.14.0-29-generi Sat Jan 10 11:12 - 13:52  (02:40)
pueblo   tty7         :0               Sat Jan  3 11:28 - 19:38  (08:10)
reboot   system boot  6.14.0-29-generi Sat Jan  3 11:27 - 19:38  (08:10)
pueblo   tty7         :0               Sat Jan  3 11:24 - 11:27  (00:03)
reboot   system boot  6.14.0-29-generi Sat Jan  3 11:17 - 11:27  (00:10)
pueblo   tty7         :0               Sat Dec 20 11:08 - 13:46  (02:38)
reboot   system boot  6.14.0-29-generi Sat Dec 20 11:07 - 13:47  (02:39)
pueblo   tty7         :0               Sun Dec 14 15:58 - crash (5+19:09)
reboot   system boot  6.14.0-29-generi Sun Dec 14 15:53 - 13:47 (5+21:53)

wtmp empieza Sun Dec 14 15:53:07 2025
```

En esta salida se nos muestran datos como: el usuario que se autentico, la terminal en que lo hizo, su ip, fecha con hora y si el usuario todavía esta logueado.

>Nótese que en el archivo dice la siguiente leyenda "wtmp empieza fecha", esto no habla desde que fecha tiene registros el archivo wtmp, el cual recordemos es el que usa el comando last para mostrarnos toda la información anterior mencionada.

Si tenemos el comando tldr instalado en nuestro sistema podremos ver mas opciones de lo que podemos hacer con el comando last.
```bash
tldr last
```

### Caso de uso en la vida real
El comando last puede ser utilizado como herramienta de investigación a la hora de administrar sistemas, supongamos que trabajamos con un colaborador que accidentalmente mando claves importantes del sistema por mera ingenuidad creyendo que nada iba a suceder, como administrador de sistemas last nos brinda la fecha y hora exacta en la que posibles usuarios responsables ingresaron al servidor, lo cual hace a last una herramienta muy potente.
### Notas Relacionadas
[[comandos-linux]]
[[lastb]]


