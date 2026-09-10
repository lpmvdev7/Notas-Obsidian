Tipo: Nota permanente
Fecha: 2026-09-02
Referencias:
* 
Temas: 
### ¿Que son los Exit Code?
Los Exit Code o codigos de salida son una serie de números que no indican si un comando que ejecutamos realizo su ejecución exitosamente o erróneamente. El código de salida 0 indica que un comando se ejecuto exitosamente, mientras que un código de salida 1 indica que ocurrió un error, ademas de estos dos existen mas códigos de salida.

```bash
| Exit code | Significado tipico                             |
| --------- | ---------------------------------------------- |
| 0         | Exito                                          |
| 1         | Error general                                  |
| 2         | Uso incorrecto del comando / error de sintaxis |
| 126       | El comando existe, pero no se puede ejecutar   |
| 127       | Comando no encontrado                          |
| 128       | Argumento invalido para exit                   |
| 128 + N   | Proceso terminado por la señal N               |
| 130       | Termino por SIGINT                             |
| 137       | Termino por SIGKILL                            |
| 143       | Termino por SIGTERM                            |
```

### ¿Como ver los exit code?
Aunque no los veamos los exit code siempre se encuentran presentes cuando interactuamos con la terminal.
```bash
ls 
echo $?
# Se imprime 0
```

La variable $? es una variable que guarda el exit code del ultimo comando ejecutado.

### Ejemplo de los exit code en bash
Mediante el uso de exit codes podemos crear un script que nos diga si un comando se instalo o no exitosamente.
```bash
#!/bin/bash
read -p "Coloca el nombre del comando que quieres instalar: " comando

sudo apt install $comando

if [ $? -eq 0 ]; then
	echo "El comando se instalo exitosamente"
	which $comando
else
	echo "$comando no se pudo instalar"
fi
```

Con los exit code podemos saber si todo nuestro script se ejecuto correctamente.
```bash
#!/bin/bash
dir="/etc"

if [[ -d "$dir" ]]; then
	echo "Es un directorio"
else
	echo "No es un directorio"
fi
	
echo "El exit code para este script es $?"
```

### Caso de uso
Crear un sript que compruebe las siguientes 4 cosas
1. Que exista el comando systemctl
2. Que el servicio ssh este activo
3. Que el directorio /tmp exista
4. Que el disco donde esta / tenga menos del 90% de uso

```bash
#!/bin/bash
systemctl_status=""
ssh_status=""
tmp_status=""
disk_status=""
overall=""
fail_count=0
exit_code=0

# Comprobar que existe el comando systemctl
which systemctl > /dev/null 
if [[ $? -eq 0 ]];then
	systemctl_status="OK"
else
	systemctl_status="FAILED"
	exit_code=1
fi

# Comprobar que ssh este activo
ssh_status_verification=$(systemctl is-active ssh)
if [[ $? -eq 0 ]]; then
	ssh_status="OK"
else
	ssh_status="FAILED"
	exit_code=2
fi


# Comprobar la existencia del directorio tmp
find / -maxdepth 1 -type d -name "tmp" > /dev/null
if [[ $? -eq 0 ]]; then
	tmp_status="OK"
else
	tmp_status="FAILED"
	exit_code=3
fi

# Comprobar que el disco / tenga menos del 90%
disk_use_verification=$(df -h / | tail -n +2 | awk '{ sub("%", "", $5); print $5 }')

if [[ "$disk_use_verification" -ge 90 ]];then
	disk_status="FAILED"
	exit_code=4
else
	disk_status="OK"
fi


# Crear un array para verificar los status
status[0]=$systemctl_status
status[1]=$ssh_status
status[2]=$tmp_status
status[3]=$disk_status

for stat in "${status[@]}"
do
	if [[ $stat == "FAILED" ]];then
		((fail_count++))
	fi
done


if [[ $fail_count -gt 0 ]];then
	overall="CRITICAL"
else
	overall="HEALTHY"	
fi

# REPORTE
echo "---------- SERVER HEALTH ---------"
echo "systemctl: $systemctl_status"
echo "ssh: $ssh_status"
echo "tmp: $tmp_status"
echo "disk: $disk_status"

echo "STATUS: $overall"

exit "$exit_code"
```

### Notas Relacionadas
[[Bash Scripting]]
[[Condicionales if en bash]]
[[Arrays en bash]]



