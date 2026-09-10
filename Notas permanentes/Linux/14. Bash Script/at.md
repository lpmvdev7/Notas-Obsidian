Tipo: Nota permanente
Fecha: 2026-09-08
Referencias:
* Linux.pdf 
Temas: #Bash-script #Automatizacion 
### ¿Que es at?
El comando at en Linux sirve para programar la ejecución de un comando o script una sola vez en el futuro.
El comando at por lo general no viene instalado en las distribuciones linux, en mi caso debido a que estoy usando una distribución basada en debían lo instalo de la siguiente manera.
```bash
sudo apt install at
```

### Uso básico del comando

#### Uso básico
El uso básico del comando es el siguiente:
```bash
at 11:00
```

El comando nos dirige a una interfaz interactiva en donde indicaremos aquellos comandos que queremos se ejecuten a la hora especificada.
```bash
at> echo "Usando at a las 11:00pm" > salida.txt
# Salimos con CTRL+D
```

Cuando sea la hora indicada podemos comprobar que el archivo ya existe.
```bash
cat salida.txt
Usando at a las 11:00pm
```

Si lo que queremos es ver aquellos jobs que at va  ejecutar corremos el siguiente comando.
```bash
# Comando que muestra una lista de todas las ejecucciones programadas con at
atq
```

#### Programar la ejecución de un script
Tenemos el siguiente script.
```bash
#!/bin/bash
echo "Hola este script fue ejecutado a las $(date)" >> scriptExecTime.txt
```

```bash
at 11:21 -f script.sh
```

```bash
cat scriptExecTime.txt 
Hola este script fue ejecutado a las mar 08 sep 2026 11:21:00 CST
```

#### Programar varias ejecuciones en un solo script
Usando at podemos programar varias ejecuciones y crear una especie de programador de tareas en bash.
```bash
#!/bin/bash
echo "Ejecucion 1" > exec.txt | at $1
echo "Ejecucion 2" >> exec.txt | at $1
echo "Ejecucion 3" >> exec.txt | at $1

```

```bash
bash script.sh 11:50
```

#### Programar la ejecución de scripts creados por nosotros
```bash
#!/bin/bash
echo "python3 script.y" | at 12:00
```

#### Uso de palabras clave 
El comando at nos permite indicar mediante palabras clave como minutes, hours o days cuando se ejecutara una script o comando.
```bash
#!/bin/bash
echo "Hola han pasado 5 minutos" > at.txt | at now + 5 minutes

echo "Hola en 1 hora" >> at.txt | at now + 1 hour

echo "Hola en 1 dia" >> at.txt | at now 1 days 
```

Con at podemos ser muy específicos con respecto a cuando queremos que se ejecute una instrucción, script o comando, podemos especificar la fecha exacta y la hora exacta de ejecución
```bash
#!/bin/bash
# HH:MM MM:DD:YYYY
echo "jelou again" > at.txt | at 12:23 09/08/2026

read -p "Coloca el DIA: " DIA
read -p "Coloca el MES: " MES
read -p "Coloca el AÑO: " YEAR

echo "jelou again" > at.txt | at 12:23 $MES/$DIA/$YEAR
```

Podemos mejorar el script de la siguiente manera:
```bash
#!/bin/bash

read -p "Coloca el DIA: " DIA
read -p "Coloca el MES: " MES
read -p "Coloca el AÑO: " YEAR
read -p "Coloca la HORA DE EJECUCION: " HORA

echo "jelou again $(date)" > at.txt | at $HORA $MES/$DIA/$YEAR
```

### Ejercicio con at
Script que reciba una hora y un comando, con esa info programar la ejecucion de ese comando usando at.
```bash
#!/bin/bash

comando=$1
hora=$2
output_file="resultado.txt"
current_date=
if [[ $# -lt 2 ]];then
	echo "Usage: $0 <command><hour>"
	exit 1
fi

echo "$comando >> $output_file" | at $hora

while [[ "$(date +%H:%M)"  != $hora  ]]
do
	echo "Esperando a que sea $hora"
	sleep 5
done

echo "$output_file esta listo"
```

```bash
bash script.sh pwd 15:56
```

>En resumen, at es una excelente herramienta de linea de comandos cuando queremos ejecutar un comando en un determinado momento.
### Notas Relacionadas
[[comandos-linux]]
[[cron]]
[[anacron]]
