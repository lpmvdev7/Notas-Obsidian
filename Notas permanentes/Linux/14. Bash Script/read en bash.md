Tipo: Nota permanente
Fecha: 2026-08-28
Referencias:
* Linux.pdf
Temas: #Bash-script #read
### ¿Para que sirve read en bash?
read nos sirve principalmente para leer datos introducidos por el usuario.

```bash
#!/bin/bash

echo "¿Cual es tu nombre?"
read nombre
echo "Hola, $nombre"
```

```bash
#!/bin/bash

read -p "Escribe tu nombre y edad:" nombre edad
echo "Nombre: $nombre"
echo "Edad: $edad"
```

### Ejercicio
Crea un script en bash llamado file_manager.sh, este script permitira al usuario realizar operaciones sobre archivos y directorios,.
El comando mostrara el siguiente menu:
1. Ver directorio actual
2. Listar archivos
3. Crear directorio
4. Crear archivo
5. Eliminar archivo
6. Mostrar información de un archivo
7. Ver permisos de un archivo
8. Salir

#### Pseudocodigo
```bash
Incio
	Establecer directorio de trabajo
	Mostrar menu de opciones
	while opcion_usuario no sea igual a 8
		si opcion_usuario es igual a 1:
			mostrar el directorio actual
		sino opcion_usuario es igual a 2:
			consultar directorio de trabajo
			mostrar el listado de archivos del directorio
		sino opcion_usuario es igual a 3:
			consultar directorio de trabajo
			crear el directorio en esa ruta
		sino opcion_usuario es igual a 4:
			consultar directorio de trabajo
			Crear un archivo en esa ruta
		sino opcion_usuario es igual a 5:
			consultar directorio de trabajo
			eliminar un archivo en esa ruta
		sino opcion_usuario es igual a 6:
			consultar directorio de trabajo
			mostrar informacion de un archivo
		sino opcion_usuario es igual a 7:
			consultar directorio de trabajo
			pedir nombre de archivo al usuario
			mostrar permisos del archivo
		sino opcion_usuario es igual a 8:
			Limpiar la consola y volver a mostrar el menu
		sino:
			volver a mostrar el menu
Fin
```

#### Bash script
En este script muestro el uso de read en linux
```bash
#!/bin/bash

echo "File Manager" | figlet | lolcat

directorio_trabajo=$PWD
echo $directorio_trabajo

menu="
	1. Ver directorio actual
	2. Listar archivos
	3. Crear directorio
	4. Crear archivo
	5. Eliminar archivo 
	6. Mostrar informacion de un archivo
	7. Ver permisos de un archivo
	8. Limpiar pantalla
	9. Salir
"
echo "$menu"

# Variable que guarda la opcion que elige el usuario
read -p "Elige una opcion del menu: " opcion_usuario

# Ciclo while del programa
while [ $opcion_usuario -ne 9 ]
do
	#echo "$menu"
	# El usuario quiere ver el directorio actual"
	if [ $opcion_usuario -eq 1 ]; then	
		echo "Directorio actual " | lolcat
		pwd
		read -p "Elige una opcion del menu: " opcion_usuario
	elif [ $opcion_usuario -eq 2 ]; then
		echo "Listar archivos" | lolcat
		echo "El listado de archivos es el siguiente:" | lolcat
		ls -l 
		read -p "Elige una opcion del menu: " opcion_usuario
	elif [ $opcion_usuario -eq 3 ]; then
		echo "Crear un nuevo directorio" | lolcat
		read -p "Coloca el nombre del nuevo directorio: " new_dir
		mkdir $new_dir
		read -p "Elige una opcion del menu: " opcion_usuario
	elif [ $opcion_usuario -eq 4 ]; then
		echo "Crear un nuevo archivo" | lolcat
		read -p "Coloca el nombre del nuevo archivo: " new_file
		touch $new_file
		read -p "Elige una opcion del menu: " opcion_usuario
	elif [ $opcion_usuario -eq 5 ]; then
		echo "Eliminar un archivo" | lolcat
		read -p "Coloca el nombre del archivo a eliminar" rm_file
		rm $rm_file
		read -p "Elige una opcion del menu: " opcion_usuario
	elif [ $opcion_usuario -eq 6 ]; then
		echo "Mostrar info de un archivo"
		read -p "Coloca el nombre del archivo " file_info
		ls -lh $file_info
		read -p "Elige una opcion del menu: " opcion_usuario
	elif [ $opcion_usuario -eq 7 ]; then
		echo "Mostrar permisos del archivo" | lolcat
		read -p "Coloca el nombre del archivo o directorio: " file_info
		ls -lh $file_info | awk '{print $1 "   " $9}'
		read -p "Elige una opcion del menu: " opcion_usuario
	elif [ $opcion_usuario -eq 8 ]; then
		clear
		echo "File Manager" | figlet | lolcat
		echo "$menu"
		read -p "Elige una opcion del menu: " opcion_usuario
	else
		read -p "Elige una opcion del menu: " opcion_usuario

	fi
done
```

Al ejecutarlo se ve de la siguiente manera:
```bash
bash file_manager.sh
```

```bash
 _____ _ _        __  __                                   
|  ___(_) | ___  |  \/  | __ _ _ __   __ _  __ _  ___ _ __ 
| |_  | | |/ _ \ | |\/| |/ _` | '_ \ / _` |/ _` |/ _ \ '__|
|  _| | | |  __/ | |  | | (_| | | | | (_| | (_| |  __/ |   
|_|   |_|_|\___| |_|  |_|\__,_|_| |_|\__,_|\__, |\___|_|   
                                           |___/           
/home/pablo/Escritorio/Estudio/linux/workdir

	1. Ver directorio actual
	2. Listar archivos
	3. Crear directorio
	4. Crear archivo
	5. Eliminar archivo 
	6. Mostrar informacion de un archivo
	7. Ver permisos de un archivo
	8. Limpiar pantalla
	9. Salir

Elige una opcion del menu: 

```
### Notas Relacionadas
[[Ciclos while en bash]]
[[Condicionales if en bash]]
[[Pseudocodigo]]
[[Bash Scripting]]


