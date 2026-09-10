Tipo: Nota permanente
Fecha: 2026-09-03
Referencias:
* Linux.pdf
Temas: #Bash-script #Argumentos-bash
### ¿Para que sirven los argumentos en bash?
Cuando ejecutamos comandos en la terminal en algunas ocasiones pasamos ciertos parámetros que modifican el comportamiento del comando, esto es lo que hacen los argumentos en bash.
Los argumentos en bash nos sirven para permitir al usuario colocar datos que afectaran el comportamiento del programa, como lo puede ser una ruta hacia un directorio o el nombre de un archivo en especifico. 

Aquí tenemos un ejemplo sencillo de argumentos en bash scripting
```bash
#!/bin/bash
echo "Hola $1"
```

```bash
bash script.sh pablo
# Hola pablo
```

Una variable especial que nos ayuda mucho al momento de trabajar con scripts que reciben argumentos en bash es $#, esta variable se encarga de verificar el numero de argumentos ingresados por un usuario en un script.
```bash
#!/bin/bash
if [[ $# -ne 2 ]];then
	echo "Necesitas al menos pasar dos argumentos"
	exit 1
fi
echo "Hola mi nombre es $1 y tengo $2 años"
```

```bash
bash script.sh
# Necesitas al menos pasar dos argumentos

bash script.sh pablo 22
# Hola mi nombre es pablo y tengo 22 años
```

### Ejemplo
Script que pida como argumento uno archivos de texto, el script debe revisar el archivo proporcionado y determinar:
* Si existe
* Si es un archivo regular
* Si tiene permisos de lectura
* Si tiene permisos de escritura

```bash
#!/bin/bash

existencia=""
regular=""
read_permiso=""
write_permiso=""
exec_permiso=""
vacio=""

# Comprobar que el usuario escribiera argumento alguno
if [[ $# -eq 0 ]];then
	echo "Ingresa la ruta a un archivo..."
	exit 1
fi

# Comprobar si el archivo existe
[[ -e $1 ]] && existencia="SI" || existencia="NO"

# Comprobar si es un archivo regular
[[ -f $1 ]] && regular="SI" || regular="NO"

# Comprobar permisos
[[ -r "$1" ]] && read_permiso="SI" || read_permiso="NO"

[[ -w "$1" ]] && write_permiso="SI" || write_permiso="NO"

[[ -x "$1" ]] && exec_permiso="SI" || exec_permiso="NO"

# Resumen
echo "Archivo Regular: $regular"
echo "Lectura: $read_permiso"
echo "Escritura: $write_permiso"
echo "Ejecuccion: $exec_permiso"
```

>NOTA: mediante la siguiente sintaxis $numero, llamamos argumentos en nuestros scripts, si por alguna razon esa sintaxis sobrepasa el numero nueve, la sintaxis cambiara a la siguiente ${numero}
```bash
$9 # Sintaxis de argumento para un digito
${12} #Sintaxis de argumentos para dos digitos
```


### Notas Relacionadas
[[Condicionales if en bash]]
[[Operadores de comparacion de archivos en bash]]


