Tipo: Nota permanente
Fecha: 2026-09-08
Referencias:
* Linux.pdf
* https://www.youtube.com/watch?v=SYAsMONYN6k
Temas: #cron #Bash-script 
### ¿Que es cron?
En sistemas linux cron se encarga de ejecutar tareas de manera automática en horarios o intervalos definidos por el usuario o el sistema. Es una herramienta muy util para automatizar scripts, respaldos, envíos de reportes o limpieza de archivos temporales.
La principal diferencia con comandos como at, es que estos comandos solo se ejecutan una vez, mientras que cron se puede ejecutar repetidamente.

### El archivo crontab
El archivo crontab es un archivo que contiene varias lineas que individualmente representan una tarea con la fecha, hora y comandos de ejecución.

La sintaxis a seguir dentro de ese archivo es la siguiente:
```bash
* * * * * comando_a_ejecutar
│ │ │ │ │
│ │ │ │ └── Día de la semana (0-6)
│ │ │ └──── Mes (1-12)
│ │ └────── Día del mes (1-31)
│ └──────── Hora (0-23)
└────────── Minuto (0-59)
```

A continuación muestro una lista de comando útiles a la hora de trabajar con cron jobs
```bash
# Editar nuestros cron jobs
crontab -e

# Listar nuestros cron jobs actuales
crontab -l

# Eliminar todos nuestros cron jobs
crontab -r

# Modificar la crontab de un usuario
crontab -u usuario -e
```

Antes de pasar a los ejemplos en los que muestro como usar cron correctamente, vale la pena analizar aquellos símbolos especiales que nos permiten crear todo tipo de cron jobs adaptados a nuestras necesidades.

| Símbolo | Significado      |
| ------- | ---------------- |
| *       | Cualquier valor  |
| ,       | Lista de valores |
| -       | Rango de valores |
| /       | Intervalos       |
### Ejemplos comunes
```bash
#m h dom mon dow

# Cron job que se ejecuta cada minuto
* * * * * /ruta/script.sh

# Cada dia a las 3:00 AM
0 3 * * * /ruta/script.sh

# Cada lunes a las 9:00 AM
0 9 * * 1 /ruta/script.sh

# Cada 15 minutos
*/15 * * * * /ruta/script.sh

# El primer dia de cada mes a medianoche
0 0 1 * * /ruta/script.sh

# De lunes a viernes a las 6:00pm
0 18 * * 1-5 /ruta/script.sh

# Cada 6 horas
0 */6 * * * /ruta/script.sh

```

### Ejercicios
Para cada ejercicio estaré trabajando con el siguiente script.
```bash
#!/bin/bash
echo "Hola cada 5 minutos $(date)" >> /tmp/script_message.log
```

```bash
# Ejecutar el script cada minuto
*/1 * * * * /home/pablo/script.sh

# Ejecutar el script todos los dias a las 2:00 AM
0 2 * * * /home/pablo/script.sh

# Ejecutar el script todos los dias a las 11:30 PM
30 23 * * * /home/pablo/script.sh

# Ejecutar el script cada hora, en el minuto 15
15 */1 * * * /home/pablo/script.sh

# Ejecutar una tarea todos los lunes a las 8:00AM
0 8 * * 1 /home/pablo/script.sh

# Ejecutar el script el dia 1 de cada mes a las 12:00PM
0 12 1 * * /home/pablo/script.sh
```

```bash
# Ejecutar una tarea a las 8:00AM, 12:00PM Y 6:00PM todos los dias
0 8,12,18 * * * /home/pablo/script.sh

# Ejecutar una tarea cada lunes, miercoles y viernes a las 7:30 AM
30 7 * * 1,3,5 /home/pablo/script.sh

# Ejecutar una tarea de lunes a viernes a las 9:00 AM
0 9 * * 1-5 /home/pablo/script.sh 

# Ejecutar una tarea de cada hora entre las 9:00AM y las 5:00PM, exactamente al comenzar cada hora.
0 9-17 * * * /home/pablo/script.sh

# Ejecutar una tarea todos los dias 1,15 y 30 de cada mes a las 10:00PM
0 22 1,15,30 * * /home/pablo/script.sh

# Ejecutar una tarea durante enero, junio y diciembre a las 6:00 AM todos los dias
0 6 * 1,6,12 * /home/pablo/script.sh
```

```bash
# Ejecutar una tarea cada 5 minutos
*/5 * * * * /home/pablo/script.sh

# Ejecutar una tarea cada 15 minutos
*/15 * * * * /home/pablo/script.sh
  
# Ejecutar una tarea cada 2 horas
0 */2 * * * /home/pablo/script.sh

# Ejecutar una tarea cada 10 minutos entre las 8:00AM y las 5:00PM
*/10 8-17 * * * /home/pablo/script.sh
  
# Ejecutar una tarea cada 30 minutos de lunes a viernes
*/30 * * * 1-5 /home/pablo/script.sh

# Ejecutar una tarea cada 20 minutos durante los meses de enero a marzo
*/20 * * 1-3 * /home/pablo/script.sh

```

```bash
# Ejecutar un script cada 5 minutos de lunea a viernes entre las 8:00 AM y las 6:00PM
*/5 8-18 * * 1-5 /home/pablo/script.sh

# Ejecutar un script todos los domingos a las 3:30AM
30 3 * * 0 /home/pablo/script.sh

# Ejecutar un script el dia 1 de cada mes a las 4:00AM
0 4 1 * * /home/pablo/script.sh

# Ejecutar un script cada 10 minutos durante todo el dia, pero unicamente de lunes a viernes.
*/10 * * * 1-5 /home/pablo/script.sh
  
# Ejecutar un script a las 9:00AM y 5:00PM todos los dias
0 9,17 * * * /home/pablo/script.sh

# Ejecutar un script cada 15 minutos entre las 6:00PM y las 11:00PM, todos los dias
*/15 18-23 * * * /home/pablo/script.sh

# Ejecutar un script cada 5 minutos los sabados y domingos.
*/5 * * * 6,0 /home/pablo/script.sh
```

```bash
# Ejecutar una tarea a las 12:00 AM del dia 1 de enero
0 0 1 1 * /home/pablo/script.sh

# Ejecutar una tarea cada 5 minutos durante febrero y marzo, unicamente de lunes a viernes.
*/5 * * 2-3 1-5 /home/pablo/script.sh
  
# Ejecutar una tarea a las 8:00, 12:00, 16:00 y 20:00 todos los dias
0 8,12,16,20 * * * /home/pablo/script.sh

# Ejecutar una tarea cada hora entre las 10:00AM y las 10:00pm, pero unicamente los sabados
0 10-22 * * 6 /home/pablo/script.sh

# Ejecutar una tarea cada 30 minutos, de lunes a viernes, durante los meses de junio, julio y agosto.
*/30 * * 6-8 1-5 /home/pablo/script.sh

```

### Caso de uso real
Para ejemplificar como funciona cron y como podemos integrarlo con los bash scripts que vayamos creando, crearemos un proyecto en el se integra un script que se ejecuta mediante cron y otro script que verifica su ejecución.

El script que se ejecutara usando cron sera el siguiente:
```bash
#!/bin/bash
echo "Cron job ejecutado a las $(date +%R)" >> /tmp/script_message.log
```

Mediante el siguiente  comando registramos nuestro cron job.
```bash
crontab -e
```

Colocamos la siguiente instrucción que dice lo siguiente:
> Ejecuta el script alojado en /usr/scripts/cronsample.sh todos los dias 9 de todos los meses.
```bash
* * 9 * * /usr/scripts/cronsample.sh
```

Al dirigirnos hacia la siguiente ruta /tmp/script_message.log, podremos ver que la ejecución de nuestro cronjob ha sido exitosa.
```bash
cat /tmp/script_message.log 
Cron job ejecutado a las 21:22
Cron job ejecutado a las 21:23
Cron job ejecutado a las 21:24
Cron job ejecutado a las 21:25
Cron job ejecutado a las 21:26
Cron job ejecutado a las 21:27
Cron job ejecutado a las 21:28
Cron job ejecutado a las 21:29
Cron job ejecutado a las 21:30
Cron job ejecutado a las 21:31
Cron job ejecutado a las 21:32
Cron job ejecutado a las 21:33
Cron job ejecutado a las 21:34
Cron job ejecutado a las 21:35
Cron job ejecutado a las 21:36
Cron job ejecutado a las 21:37
```

Como forma de comprobar que el script funciona, pensé que podríamos crear un script que cuenta todas las lineas del archivo /tmp/script_message.log, ya que cada linea registrada en este archivo, representa la ejecución exitosa del script original.

El script para leer este archivo se veria de la siguiente manera:
```bash
#!/bin/bash

count_cron=$(cat /tmp/script_message.log | wc -l)
echo "$count_cron"
```

Al ejecutar el scrip podemos ver el numero de lineas que contiene el archivo /tmp/script_message.log y de esta manera comprobar que la ejecución del cron job original ha sido exitosa.
```bash
croncount.sh
20
```

Este ejemplo puede ser incluso mas complejo, pero sirve para mostrar de forma clara como los cron jobs se integran al flujo de trabajo de los bash scripts y como junto con estos podemos crear mejores herramientas que nos ayuden en nuestros trabajos.
### Notas Relacionadas
[[Automatizacion en linux]]
[[at]]
[[anacron]]