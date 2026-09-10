Tipo: Nota permanente
Fecha: 2026-09-07
Referencias:
* Linux.pdf
Temas: #Funciones #Bash-script #Modularizacion
### ¿Que son las funciones en bash script?
Las funciones en bash scripting son bloques de codigo reutilizable que nos ayudan a usar la misma lógica para resolver el mismo problema en varias partes diferentes de nuestros scripts. Esto nos permite escribir programas mas robustos y mantenibles a largo plazo.

La sintaxis mas común para crear funciones en bash script es la siguiente:
```bash
saludar(){
	echo "Hola mundo"
}
```

Las funciones pueden recibir varios argumentos, esto se asemeja a la forma en que trabajamos en lenguajes como python o javascript.
```bash
#!/bin/bash
saludar(){
	echo "Hola $1, tienes $2 años y vives en $3"
}
saludar "Pablo" 24 "Mexico"
```

Mediante la palabra reservada return, las funciones bash puden devolver valores, como por ejemplo un status code.
```bash
#!/bin/bash
comprobar_archivo(){
	if [[ -f "$1" ]]; then
		return 0
	else
		return 1
	fi
}

comprobar_archivo "/etc/passwd"
if [[ $? -eq 0 ]]; then
	echo "El archivo existe"
else
	echo "El archivo no existe"
fi

```

Cuando creamos funciones en bash y en cualquier otro lenguaje de programación, prácticamente estamos creando un ámbito nuevo en el que vivirá una parte de nuestro código, en bash esto no significa que ese código sea accesible únicamente para esa función, para que una variable sea accesible únicamente por la función en la que fue creada usamos la palabra reservada local.
```bash
#!/bin/bash
saludar(){
	local nombre="Pablo"
	echo "Hola $nombre"
}
saludar
```

### Ejercicios
#### Ejercicio 1
Somos administradores de un servidor de producción y necesitamos un script que verifique periódicamente el estado de recursos críticos y alerte si algo esta mal.
* Necesitamos verificar el disco y revisar el uso de todos los discos montados supera el umbral especificado por el administrador.
* Necesitamos calculara el porcentaje de RAM usada, se retornara un código de salida 0 en caso de que la RAM usado sea menor al 80%, un 1 si supera el 80% y un 2 si supera el 95%.
* Necesitamos verificar los servicios disponibles en el servidor, es decir nginx, sshd y otros, verificar si estan activos, en caso de que no estén activos se deben intentar reiniciar y loguear el resultado.
* El script principal debe aceptar los servicios a monitorear como argumentos.

```bash
#!/bin/bash
regex='\b[0-9]{1,}\b'
regexTwo='\b\[0-9]{1,2}\b'

# Funcion que verifica los discos montados

checkDisk(){
	local numeros=$(df -h | awk 'NR>1 {print $5}' | grep -Eo "$regex")
	for numero in $numeros
	do
		if [[ $numero > $1 ]];then
			echo "No se ha superado el umbral"
		fi
	done
}

checkRam(){
	local totalRAM=$(cat /proc/meminfo | awk 'NR==1 { print $2 }')
	local availableRAM=$(cat /proc/meminfo | awk 'NR==3 { print $2 }')
	
	# Memoria RAM usada
	local usedRAM=$(( totalRAM - availableRAM ))
	local porcentajeRAM=$(( (usedRAM * 100) / totalRAM ))
	
	if [[ $porcentajeRAM -lt 80 ]];then
		echo "$porcentajeRAM"
	elif [[ $porcentajeRAM -gt 80 ]]; then
		echo "$porcentajeRAM"
	elif [[ $porcentajeRAM -ge 95 ]]; then
		echo "$porcentajeRAM"
	fi
}

checkService(){
	systemctl list-unit-files "$1.service" >/dev/null
	if [[ $? -eq 0 ]]; then
		systemctl restart $1
		echo "Reiniciando servicio...."
	fi
}

checkDisk 69
checkRam
checkService nginx

```
### Notas Relacionadas
[[Funciones]]
[[Variable especiales en bash]]

