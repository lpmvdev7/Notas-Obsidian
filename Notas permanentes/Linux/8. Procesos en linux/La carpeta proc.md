Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf 
Temas: #Procesos 
### ¿Que es la carpeta proc?
La carpeta proc es un directorio con archivos temporales generados por el sistema operativo, estos archivos temporales corresponden a los procesos en ejecución dentro del sistema.  Cuando ejecutamos un comando, automáticamente se crea un directorio dentro de esta carpeta, en este directorio viene información importante sobre el proceso que se ejecuto como la linea exacta, su estado, el directorio en donde se ejecuto y mucha mas información.

>La carpeta proc es la carpeta encargada de guardar toda la información relacionada a los procesos en ejecuccion.

```bash
cd /proc
```

### Ejemplo de la proc
Para ver la carpeta proc en acción ejecutamos el comando sleep en segundo plano.
```bash
sleep 500&
```

Miramos cual es su id de proceso
```bash
jobs -p
11272
```

Ahora que conocemos el id nos dirigimos a la carpeta /proc y allí encontraremos un directorio con el nombre del id.
```bash
cd /proc/11272
```

Una vez dentro de esta carpeta podemos sacar información importante del proceso en ejecución como la linea exacta que lo empezó
```bash
cat cmdline 
sleep500
```

El directorio actual de trabajo del proceso
```bash
ls -lh cwd
lrwxrwxrwx 1 pablo pablo 0 jul 31 11:03 cwd -> /home/pablo
```

Un desglose del estado actual del proceso
```bash
cat status 
Name:	sleep
Umask:	0002
State:	S (sleeping)
Tgid:	11272
Ngid:	0
Pid:	11272
....
```

Un enlace simbólico al binario del comando ejecutado.
```bash
ls -lh exe
lrwxrwxrwx 1 pablo pablo 0 jul 31 11:03 exe -> /usr/bin/sleep
```

### Información de memoria en la carpeta proc
La carpeta proc al ser el hogar de todos los procesos en ejecución, nos proporciona de un archivo con información relacionada a la memoria del sistema.
```bash
cat /proc/meminfo
MemTotal:        4475732 kB
MemFree:         2636696 kB
MemAvailable:    3419704 kB
Buffers:           57592 kB
Cached:           936160 kB
SwapCached:            0 kB
Active:          1255944 kB
Inactive:         312584 kB
Active(anon):     604884 kB
Inactive(anon):        0 kB
Active(file):     651060 kB
Inactive(file):   312584 kB
Unevictable:          48 kB
```

### Notas Relacionadas
[[Sistema de archivos]]
[[bg]]
[[jobs]]
[[Soft-links]]



