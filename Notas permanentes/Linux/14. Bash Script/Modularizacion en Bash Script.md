Tipo: Nota permanente
Fecha: 2026-09-07
Referencias:
* 
Temas: #Modularizacion #Bash-script 
### ¿Que es la modularizacion?
La modularizacion en Bash Script consiste en dividir un script grande en partes pequeñas, independientes y reutilizables.  Modularizar nos ayuda a separar responsabilidades y tener código mas mantenible a lo largo del tiempo.

Pasamos de esto..
```bash
#!/bin/bash
# 300 lineas de codigo
```

A esto
```bash
mi-cli/
├── main.sh
├── utils.sh
├── services.sh
├── files.sh
└── config.sh
```

### ¿Porque es importante modularizar?
Supongamos que estamos creando una herramienta para administrar servidores, esta herramienta es una cli que tiene 4 subcomandos principales: status, disk, services y logs.

Todo podría vivir en un archivo principal llamado serverctl.sh
```bash
#!/bin/bash

# Funciones de servicios
# Funciones de disco
# Funciones de logs
# Funciones de red
# ....
```

La estructura funciona, pero conforme el proyecto avanza y queremos añadir mas funcionalidades necesitamos empezar a separar responsabilidades, por ejemplo de la siguiente manera:
```bash
serverctl/
├── main.sh
├── services.sh
├── disk.sh
├── network.sh
└── utils.sh
```

De esta manera coordinamos todo desde main.sh

### ¿Como modularizar?
La modularizacion en bash ocurre mediante el uso del comando, source.

Tenemos un pequeño archivo llamado utils.sh
```bash
#!/bin/bash
utils.sh

saludar(){
	echo "Hola desde utils.sh"
}
```

Desde otro archivo llamamos a utils.sh
```bash
#!/bin/bash
source ./utils.sh

saludar
```

### Ejemplos
#### Calculadora modular
Crear una calculadora que le permita al usuario realizar alguna de las operaciones aritméticas básicas, es decir suma, resta, multiplicación o división.
```bash
calculadora/
├── main.sh
├── operaciones.sh
```

```bash
# operaciones.sh
suma(){
	local operacion=$(expr $1 + $2)
	echo "$operacion"
}


resta(){
	local operacion=$(expr $1 - $2)
	echo "$operacion"
}

multiplicacion(){
	local operacion=$(expr $1 \* $2)
	echo "$operacion"
}

dividir(){
	local operacion
	if [[ $2 -eq 0 ]];then
		echo "No se puede dividr entre 0"
	else
		operacion=$(expr $1 / $2)
		echo $operacion
	fi
}

#suma 10 10
#resta 30 10
#multiplicacion 10 20
#dividir 10 10

```

```bash
#!/bin/bash
# main.sh
source ./operaciones.sh

read -p "Coloca un numero: " num1
read -p "Coloca otro numero: " num2
read -p "Coloca la operacion que quieres realizar (+, -, *, /)." operacion

case "$operacion" in
	"+") resultado=$(suma $num1 $num2);;
	"-") resultado=$(resta $num1 $num2);;
	"*") resultado=$(multiplicacion $num1 $num2);;
	"/") resultado=$(dividir $num1 $num2);;
esac

echo "$resultado"
```

#### Monitor de servicios
La estructura del proyecto debe ser la siguiente:
```bash
service-monitor/
├── main.sh
└── lib/
    ├── services.sh
    └── utils.sh
```

En el modulo de **services.sh** únicamente nos encargaremos de trabajar con los servicios verificando si estan activos o si existen.
En el modulo de **utils.sh** colocaremos funcionalidades adicionales en base a los resultados de services.sh.
Por ultimo dentro de main.sh tendremos el punto de entrada de la aplicación. Aqui recibimos servicios como argumentos, comprobamos cada servicio y mostramos su estado al usuario final. El archivo main.sh se encarga de coordinar la logica no de implementarla.

```bash
.
├── lib
│   ├── services.sh
│   └── utils.sh
└── main.sh
```

```bash
#!/bin/bash
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"

source "${SCRIPT_DIR}/lib/utils.sh"
source "${SCRIPT_DIR}/lib/services.sh"

if [[ $# -eq 0 ]]; then
	echo "Usage: $0 <services>"
	exit 1
fi	


services=("$@")

for servicio in "${services[@]}"
do
	service_exists_comunicate "$servicio"
done
```

```bash
#!/bin/bash

LIB_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
source "${LIB_DIR}/services.sh"

# Funciones que indican al usuario que existe un servicio o no
service_exists_comunicate(){
	service_exists $1
	if [[ $? -eq 0 ]];then
		echo "[OK] $1 esta activo"
	else
		echo "[ERROR] $1 no esta instalado"
	fi
}
```

```bash
#!/bin/bash

# Verificar la existencia de un servicio
service_exists(){
	local exit_code
	sudo systemctl list-unit-files "$1.service" >/dev/null
	if [[ $? -eq 0 ]];then
		exit_code=0
		return $exit_code
	else
		exit_code=1
		return $exit_code
	fi
}

# Verificar el status de un servicio
service_status(){
	local exit_code
	service_exists $1
	if [[ $? -eq 0 ]];then
		exit_code=0
		systemctl is-active $1 >/dev/null
		return $exit_code
	else
		exit_code=1
		return $exit_code
	fi
}
```
### Notas Relacionadas
[[Funciones en Bash Script]]
[[Funciones]]


