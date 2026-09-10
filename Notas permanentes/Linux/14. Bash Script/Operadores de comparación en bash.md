Tipo: Nota permanente
Fecha: 2026-08-29
Referencias:
* Linux.pdf
Temas: #Bash-script #Operadores-comparacion 
### ¿Cuales son los operadores de comparación en bash?
Los operadores de comparación en bash cumplen diferentes funciones dependiendo si estamos comparando números o cadenas.

En caso de que estemos comparando números los operadores de comparación se verían de la siguiente manera.

```bash
| Operador | Significado      |
| -------- | ---------------- |
| -eq      | equal            |
| -ne      | not equal        |
| -gt      | greater than     |
| -ge      | greater or equal |
| -lt      | less than        |
| -le      | less or equal    |
```

En caso de que estemos comparando texto, los operadores de comparación siguen siendo los mismos de toda la vida pero agregando algunos mas.
```bash
| Operador | Significado     |
| -------- | --------------- |
| =        | igualdad        |
| !=       | diferencia      |
| <        | menor que       |
| >        | mayor que       |
| -z       | cadena vacia    |
| -n       | cadena no vacia |
```

### Ejemplos con operadores de comparación numéricos
Un script que le pida dos números al usuario y en base a ellos le indique si estos son iguales.
```bash
# Pseudocodigo
Inicio
	pedir primer numero al usuario
	pedir segundo numero al usuario
	si el primer y segundo numero del usuario son iguales:
		imprimir "Los numeros son iguales"
	sino:
		imprimir "Los numeros no son iguales"
Fin
```

```bash
#!/bin/bash
read -p "Introduce el primer numero " numero_uno
read -p "Introduce el segundo numero "  numero_dos

if [ $numero_uno -eq $numero_dos ]; then
	echo "Los numeros son iguales"
else:
	echo "Los numeros no son iguales"
fi

```

Un script que pida la calificación de 0 al 100, si la calificación es mayor o igual a 60 el alumno esta aprobado, de lo contrario esta reprobado.

```bash
# Pseudocodigo
Inicio
	Mensaje mostrando como funciona el sistema de calificaciones
	sistema pide calificacion al usuario
	si calificacion_usuario mayor o igual a 60:
		mostrar mensaje "El alumno esta aprobado"
	sino:
		mostrar mensaje "El alumno esta reprobado"
Fin
```

```bash
#!/bin/bash

read -p "Ingresa tu calificacion del 0 al 100: " calificacion
aprobatoria=60

if [ $calificacion -ge $aprobatoria ]; then
	echo "El alumno esta aprobado"
else
	echo "El alumno esta reprobado"
fi
```

### Ejemplos con operadores de comparación de cadenas
Script que sirva como sistema de autenticación, el sistema debe pedir usuario y contraseña, los únicos datos validos son el usuario: admin y la contraseña bash123.
El script debe ser capaz de detectar lo siguiente:
* Un usuario vacio
* Contraseña vacia
* Usuario incorrecto
* Contraseña incorrecta
* Ambos correctos
* Permitir tres intentos al usuario
```bash
Inicio
	Mientras intentos diferente a 3:
		Sistema pide usuario
		Sistema pide constraseña
		Si usuario y constraseña no estan vacios:
			Si usuario igual a usistema y contraseña igual a csistema:
				mostrar mensaje "Bienvenido al sistema"
				variable intentos igual a 3
			Sino usuario diferente a usistema:
				mostrar mensaje "El usuario no es valido"
				variable intentos incrementa en 1
			Sino contraseña diferente a csistema:
				mostrar mensaje "La contraseña no es valida"
				variable intentos incrementa en 1
		Sino usuario vacio:
			mostrar mensaje "El usuario esta vacio"
			variable intentos incrementa en 1
		Sino:
			mostrar mensaje "La contraseña esta vacio"
			variable intentos incrementa en 1
Fin
```

```bash
#!/bin/bash

usuario_sistema="admin"
password_sistema="bash123"
intentos=0

while [ $intentos -ne 3 ]
do
        read -p "Ingresa al usuario: " usuario_input
        read -p "Ingresa la contrasena: " password_input
        if [[ -n $usuario_input && -n $password_input ]]; then
                if [[ $usuario_input = $usuario_sistema && $password_input = $password_sistema ]];then
                        echo "Bienvenido al sistema"
                        ((intentos=3))
                elif [ $usuario_input != $usuario_sistema ]; then
                        echo "el usuario no es valido"
                        ((intentos++))
                elif [ $password_input != $password_sistema ]; then
                        echo "La contrasena no es valida"
                        ((intentos++))
                fi
        elif [ -z $usuario_input ]; then
                echo "El usuario esta vacio"
                ((intentos++))
        else
                echo "La contrasena esta vacia"
                ((intentos++))
        fi
done
```
### Notas Relacionadas
[[Operadores de comparacion]]
[[Operadores de comparación en bash]]

