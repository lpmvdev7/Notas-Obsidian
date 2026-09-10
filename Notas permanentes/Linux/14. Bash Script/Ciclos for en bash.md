Tipo: Nota permanente
Fecha: 2026-09-01
Referencias:
* 
Temas: #Ciclo-for #Bash-script 
### ¿Para que sirve?
En bash los ciclos for nos permiten repetir un bloque de instrucciones un numero determinado de veces o para recorrer una lista de elementos (como números, cadenas, nombres de archivos, etc.) y ejecutar un conjunto de comandos para cada uno de ellos.
El for nos es útil cuando queremos automatizar tareas repetitivas sin la necesidad de escribir el mismo código varias veces.

```bash
#!/bin/bash
for number in 1 2 3 4 5 6 7
do
	echo $number
done
```

```bash
#!/bin/bash
for number in {1..10}
do
	echo $number
done
```

```bash
#!/bin/bash
frutas=("Manzana" "Pera" "Naranja" "Platano")
for fruta in "${frutas[@]}"; 
do
	echo "Fruta: $fruta"
done
```

### Ejemplos de uso
Imprimir los números pares a partir de un rango
```bash
#!/bin/bash
for numero in {1..20}
do
	if (( numero % 2 == 0 )); then
		echo $numero
	fi
done
```

Solicitar un numero al usuario y mostrar su tabla de multiplicar.
```bash
#!/bin/bash
read -p "Coloca un numero " numero
for number in $(seq 1 $numero)
do
	echo "$numero x $number = $(( numero * number ))"
done
```

### Caso de uso final con for
Crear un script el cual reciba como argumento la ruta de un directorio, el programa debe recorrer todos los elementos que se encuentren directamente dentro del directorio y analizar cada uno.
Para cada elemento debe determinar:
* Si es un archivo regular
* Si es un directorio
* Si es un enlace simbólico
* Si el archivo regular tiene permisos de lectura
* Si tiene permisos de escritura
* Si tiene permisos de ejecución
Al finalizar, el script debe mostrar en stdout un reporte que contenga la siguiente información:
* El directorio analizado
* Mostrar la cantidad de archivos regulares, directorios y enlaces simbólicos existentes.
* Mostrar la cantidad de archivos con permisos de lectura, escritura y ejecución.

```bash
#!/bin/bash

ruta="$PWD"
archivos_regulares=0
directorios=0
enlaces_simbolicos=0
p_lectura=0
p_escritura=0
p_ejecucion=0

if [[ -d "$ruta" ]]; then

    for elemento in "$ruta"/*
    do
        if [[ -L "$elemento" ]]; then

            ((enlaces_simbolicos++))

        elif [[ -d "$elemento" ]]; then

            ((directorios++))

        elif [[ -f "$elemento" ]]; then

            ((archivos_regulares++))

            if [[ -r "$elemento" ]]; then
                ((p_lectura++))
            fi

            if [[ -w "$elemento" ]]; then
                ((p_escritura++))
            fi

            if [[ -x "$elemento" ]]; then
                ((p_ejecucion++))
            fi

        fi
    done

    echo "---------- Resumen Final ----------"
    echo "Archivos Regulares: $archivos_regulares"
    echo "Directorios: $directorios"
    echo "Enlaces simbolicos: $enlaces_simbolicos"
    echo "Archivos con permisos de lectura: $p_lectura"
    echo "Archivos con permisos de escritura: $p_escritura"
    echo "Archivos con permisos de ejecucion: $p_ejecucion"

else

    echo "Se necesita un directorio"

fi
```

### Notas Relacionadas
[[Ciclo for]]


