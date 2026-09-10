Tipo: Nota permanente
Fecha: 2026-08-31
Referencias:
* Linux.pdf
Temas: #Condicionales #Bash-script 
### ¿Para que sirven los condicionales if en bash?
Los condicionales if nos ayudan a controlar el flujo de una aplicación dependiendo de si algo se cumple o no, esto nos permite aplicar lógica compleja y crear soluciones mas robustas.

### Uso de los condicionales
```bash
# Sintaxis basica de un condicional en bash
if [ condicion ]; then
	#Accion
else
	#Accion	
fi

# Sintaxis mas robusta y la que yo recomiendo usar
if [[ condicion ]]; then
	#Accion
fi

```

### Ejemplos de condicionales en bash

Un script que pide un numero al usuario y determina si este es positivo, negativo o cero, mostrando el resultado
```bash
#!/bin/bash
read -p "Coloca un numero: " numero_usuario

if [[ $numero_usuario -gt 0 ]]; then
	echo "Numero positivo"
elif [[ $numero_usuario -lt 0 ]]; then
	echo "Numero negativo"
else
	echo "Es cero"
fi
```

Un script que verifique la existencia de una ruta, esto nos podría servir para verificar la existencia de un comando.
```bash
#!/bin/bash
read -p "Escribe el comando que quieres buscar: " comando

ruta="/usr/bin/$comando"

if [[ -e "$ruta" ]]; then
	echo "El comando existe y se encuentra en: $(which $comando)"
else
	echo "El comando no existe"
fi
```

Dado un archivo como argumento, determina e imprime si es legible, escribible, ejecutable, un enlace simbólico, un directorio, o no existe.
```bash
# Pseudocodigo
Inicio
	variable lectura
	variable escritura
	variable ejecucion
	variable tipo
	Recibir ruta como argumento
	Si ruta existe:
		Si ruta es directorio:
		tipo="dir"
			Si ruta tiene permiso lectura:
				lectura="r"
			Si no
				lectura="-"
			Si ruta tiene permiso escritura:
				escritura="w"
			Si no
				escritura="-"
				
			Si ruta tiene permisos ejecucion:
				ejecucion="x"
			Si no
				ejecuccion="-"
		Sino ruta es symlink:
			tipo="symlink"
			Si ruta tiene permiso lectura:
				lectura="r"
			Si no
				lectura="-"
			Si ruta tiene permiso escritura:
				escritura="w"
			Si no
				escritura="-"
				
			Si ruta tiene permisos ejecucion:
				ejecucion="x"
			Si no
				ejecuccion="-"
		Sino
			tipo="File"
			Si ruta tiene permiso lectura:
				lectura="r"
			Si no
				lectura="-"
			Si ruta tiene permiso escritura:
				escritura="w"
			Si no
				escritura="-"
				
			Si ruta tiene permisos ejecucion:
				ejecucion="x"
			Si no
				ejecuccion="-"
			
		variable permisos = lectura+escritura+ejecucion	
		Mostrar "Archivo de tipo: tipo tiene los siguientes permisos: permisos"
			
	Sino
		Mostrar mensaje "El archivo no existe"
Fin
```

```bash
#!/bin/bash

lectura=""
escritura=""
ejecucion=""
tipo=""
ruta="$1"

if [[ -e "$ruta" ]]; then
	
	
	if [[ -d "$ruta" ]]; then
		tipo="directorio"
		
		if [[ -r "$ruta" ]]; then
			lectura="r"
		else
			lectura="-"
		fi


		if [[ -w "$ruta" ]]; then
			escritura="w"
		else
			escritura="-"
		fi


		if [[ -x "$ruta" ]]; then
			ejecucion="x"
		else
			ejecucion="-"
		fi
	
	elif [[ -L "$ruta" ]]; then
		tipo="Link"
		if [[ -r "$ruta" ]]; then
                        lectura="r"
                else
                        lectura="-"
                fi


                if [[ -w "$ruta" ]]; then
                        escritura="w"
                else
                        escritura="-"
                fi


                if [[ -x "$ruta" ]]; then
                        ejecucion="x"
                else
                        ejecucion="-"
                fi
	else
		tipo="File"
		if [[ -r "$ruta" ]]; then
                        lectura="r"
                else
                        lectura="-"
                fi


                if [[ -w "$ruta" ]]; then
                        escritura="w"
                else
                        escritura="-"
                fi


                if [[ -x "$ruta" ]]; then
                        ejecucion="x"
                else
                        ejecucion="-"
                fi


	fi	
	permisos="$lectura$escritura$ejecucion"
	echo "Archivo: $tipo"
	echo "Permisos: $permisos"
else
	echo "El archivo no existe"
fi
```
### Notas Relacionadas
[[Condicionales]]


