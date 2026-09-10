Tipo: Nota permanente
Fecha: 2026-08-29
Referencias:
* Linux.pdf
Temas: #Bash-script #Operadores-comparacion 
### ¿Que son los operadores de comparación de archivos en bash?
Los operadores de comparación de archivos en bash nos ayudan a verificar varias características relacionadas a archivos en sistemas unix, como lo seria linux. Por ejemplo estos operadores nos ayudan a verificar la existencia de archivos, directorios o rutas en nuestro sistema de archivos.

Estos serian los operadores mas usados en bash scripting en relación a archivos.
```bash
| Operador | Significado            |
| -------- | ---------------------- |
| -e       | existe                 |
| -f       | es un archivo regular  |
| -d       | es un directorio       |
| -r       | se puede leer          |
| -w       | se puede escribir      |
| -x       | se puede ejecutar      |
| -s       | no esta vacio          |
| -L       | es un enlace simbolico |
```

### Usos de cada operador
Con -e podemos comprobar si una ruta existe, independientemente de si es archivo, directorio, enlace, etc.
```bash
#!/bin/bash

ruta="/etc/passwd"
if [[ -e "$ruta" ]]; then
	echo "La ruta existe"
else
	echo "La ruta no existe"
fi
```

Con -f comprobamos que la ruta existe y esta corresponde a un archivo regular.
```bash
#!/bin/bash

ruta="/etc/passwd"
if [[ -f "$ruta" ]]; then
	echo "$ruta es un archivo regular"
else
	echo "La ruta no existe"
fi
```

Con -d comprobamos si la ruta corresponde a un directorio.
```bash
#!/bin/bash
directorio="/home/pablo/Escritorio/Universidad"
if [[ -d "$directorio" ]]; then
	echo "$directorio es un directorio"
else
	echo "$directorio no es un directorio"
fi
```

Con -r podemos comprobar si el usuario que ejecuta el script tiene permiso de lectura sobre la ruta.
```bash
#!/bin/bash
archivo="/etc/passwd"
if [[ -r "$archivo" ]]; then
	echo "Puedes leer $archivo"
else:
	echo "No puedes leer $archivo"
fi
```

Con -w podemos comprobar si un usuario tiene permisos de escritura sobre una ruta.
```bash
#!/bin/bash
archivo="datos.txt"
if [[ -w "$archivo" ]]; then
	echo "Puedes escribir en $archivo"
else
	echo "No puedes escribir en $archivo"
fi
```

Con -x podemos comprobar si tenemos permisos de ejecución sobre una ruta, esto nos puede ser de utilidad para comprobar scripts y programas.
```bash
#!/bin/bash
archivo="script.sh"
if [[ -x $archivo ]]; then
	echo "$archivo se puede ejecutar"
else
	echo "$archivo no se puede ejecutar"
fi
```

### Ejemplo
Tenemos un script que debe hacer una copia de seguridad de un archivo importante.

El usuario ejecuta 
```
./backup_check.sh archivo.txt
```
Tu programa debe determinar si ese archivo esta en condiciones de ser respaldado mediante las siguientes reglas.
El programa debe analizar la ruta recibida y decidir que hacer:
* Si no existe, debe informar del problema
* Si es un directorio, debe rechazarlo
* Si no es un archivo regular, debe rechazarlo
* Si no tiene permiso de lectura, debe rechazarlo
* Si no tiene permiso de escritura, debe mostrar una advertencia.
* Si el archivo esta vació, debe rechazarlo
* Si tiene permiso de ejecución, debe indicarlo
* Si es un enlace simbólico, debe indicarlo

```bash
Inicio
	variable ruta
	variable ruta_existente
	variable directorio
	variable archivo_regular
	variable permisos_lectura
	variable permisos_escritura
	variable vacio
	variable permisos_ejecuccion
	variable symlink
	
	Si ruta existe:
		ruta_existente = SI
	Sino
		ruta_existente = NO
		Mostrar mensaje "La ruta es inexistente"
		Salir del programa
		
	Si ruta es un directorio:
		directorio = SI
		Mostrar mensaje "La ruta corresponde a un directorio"
		Salir del programa
	Sino
		directorio = NO
	
	Si ruta es un archivo regular
		archivo_regular = SI
	Sino
		archivo_regular = NO
		Mostrar mesnaje "La ruta corresponde a un archivo que no es regular"
		Salir del programa
	
	Si ruta tiene permisos de lectura
		permisos_lectura = SI
	Sino
		permisos_lectura = NO
		Mostrar mensaje "La ruta no tiene permisos de lectura"
		Salir del programa
		
	Si ruta tiene permisos de escritura
		permisos_escritura = SI
	Sino
		permisos_escritua = NO
	
	Si ruta esta vacio:
		vacio = SI
		Mostrar mensaje "El archivo esta vacio"
		Salir del programa
	Sino
		vacio = NO
	
	Si ruta tiene permisos de ejecuccion
		permisos_ejecuccion = SI
	Sino 
		permisos_ejecuccion = NO
	
	Si ruta es un symlink
		symlink = SI
	Sino
		symlink = NO
	
	Mostrar informacion de las variables como reporte al usuario
	
Fin
```

```bash
#!/bin/bash

ruta="/home/pablo/menu.txt"
ruta_existente=""
directorio=""
archivo_regular=""
permisos_lectura=""
permisos_escritura=""
vacio=""
permisos_ejecuccion=""
symlink=""

if [[ -e "$ruta" ]]; then
	ruta_existente="SI"
else
	echo "La ruta es inexistente"
	exit 1
fi


if [[ -d "$ruta" ]]; then
	echo "La ruta corresponde a un directorio"
	exit 1
else
	directorio="NO"
fi



if [[ -f "$ruta" ]]; then
	archivo_regular="SI"
else
	echo "La ruta corresponde a un archivo que no es regular"
	exit 1
fi

if [[ -r "$ruta" ]]; then
	permisos_lectura="SI"
else
	echo "La ruta no tiene permisos de lectura"
	exit 1
fi

if [[ -w "$ruta" ]]; then
	permisos_escritura="SI"
else
	permisos_escritura="NO"
fi

if [[ -s "$ruta" ]]; then
	vacio="NO"
else
	echo "El archivo esta vacio"
	exit 1
fi

if [[ -x "$ruta" ]]; then
	permisos_ejecuccion="SI"
else
	permisos_ejecuccion="NO"
fi


if [[ -L "$ruta" ]]; then
	symlink="SI"
else
	symlink="NO"
fi

echo "----------- REPORTE FINAL -------------------"
echo "Existe la ruta: $ruta_existente"
echo "Directorio: $directorio"
echo "Archivo regular: $archivo_regular"
echo "Permisos lectura: $permisos_lectura"
echo "Permisos escritura: $permisos_escritura"
echo "Permisos ejecuccion: $permisos_ejecuccion"
echo "vacio: $vacio"
echo "symlink: $symlink"

```

### Notas Relacionadas
[[Operadores de comparacion]]


