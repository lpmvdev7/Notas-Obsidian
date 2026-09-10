Tipo: Nota permanente
Fecha: 2026-09-01
Referencias:
* 
Temas: #Arrays #Bash-script 
### ¿Que son los arrays en bash?
En bash los arrays son estructuras que nos permiten almacenar multiples valores dentro de una misma variable. Son especialmente utiles cuando trabajamos con listas de archivos, directorios, procesos, comandos, usuarios, argumentos, etc.

La forma mas sencilla de crear un array es la siguiente:
```bash
frutas=("Manzana" "pera" "naranja" "uva")
```

### Ejemplos de uso
En este ejemplo estamos imprimiendo el primer elemento del array
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")
echo "${sistemas_operativos[0]}"
#Linux
```

En este ejemplo obtenemos todos los elementos
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")
echo "${sistemas_operativos[@]}"
```

La manera mas usada de obtener los elementos de un array en bash es mediante un ciclo for.
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")
for os in "${sistemas_operativos[@]}"
do
	echo "$os"
done
```

También podemos verificar cuantos elementos tiene un array
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")
echo "${#sistemas_operativos[@]}"
```

En base a saber cuantos elementos tiene un array podemos crear un ciclo for.
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")

for ((i=0; i<${#sistemas_operativos[@]}; i++)); do
    echo "${sistemas_operativos[i]}"
done
```

Cambiar un elemento por otro
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")
sistemas_operativos[2]="Unix"
echo "${sistemas_operativos[2]}"
```

Agregar elementos
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")

# Agregar un elemento al array de sistemas operativos
sistemas_operativos+=("BDS")

for os in "${sistemas_operativos[@]}"
do
	echo "$os"
done
```

Crear elementos en posiciones especificas
```bash
sistemas_operativos=("Linux" "MacOS" "Windows")

# Crear un elemento en una zona especifica
sistemas_operativos[5]="Fedora"

echo "${sistemas_operativos[5]}"
echo "${!sistemas_operativos[@]}"
```

Obtener indices
```bash
#/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")

sistemas_operativos[5]="Fedora"

# Obtener todos los indices de los elementos en el array
echo "${!sistemas_operativos[@]}"
```

Recorrer un array e imprimir indices y valores.
```bash
#!/bin/bash
sistemas_operativos=("Linux" "MacOS" "Windows")
for indice in "${!sistemas_operativos[@]}"; do
    echo "$indice -> ${sistemas_operativos[$indice]}"
done
# 0 -> Linux
# 1 -> MacOS
# 2 -> Windows
```

Eliminar elementos, es importante saber que al hacer esto el indice se elimina junto con el elemento.
```bash
sistemas_operativos=("Linux" "MacOS" "Windows")
unset 'sistemas_operativos[2]'
```

### Caso practico
Crea un script que analice el estado de varios servicios de Linux
* nginx
* ssh
* docker
* cron
Se tiene que hacer lo siguiente:
* Recorrer el array comprobando el estado de cada servicio, determinando si esta ACTIVO, INACTIVO o NO INSTALADO.
* Al final mostrar un pequeño resumen mostrando informacion relacionada al numero de servicios analizados, numero de servicios activos, inactivos y no instalados.

```bash
#!/bin/bash
servicios=("nginx" "ssh" "docker" "cron" "mysql")
activos=0
inactivos=0
no_instalados=0
analyzed=0
for servicio in "${servicios[@]}"
do
	if [[ "$(systemctl is-active "$servicio")" == "active" ]]; then
		echo "$servicio : activo"
		((activos++))
	elif [[ "$(systemctl is-active "$servicio")" == "inactive" ]]; then
		((inactivos++))
		echo "$servicio : inactivo"
	else
		((no_instalados++))
	fi
	((analyzed++))
done

echo "Servicios analizados: $analyzed"
echo "Servicios activos: $activos"
echo "Servicios inactivos: $inactivos"
echo "Servicios no instalados: $no_instalados" 
```

### Notas Relacionadas
[[Arrays asociativos en bash]]



