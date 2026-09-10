Tipo: Nota permanente
Fecha: 2026-08-31
Referencias:
* 
Temas: #Switch-case #Condicionales #Bash-script  
### ¿Para que sirve switch en bash?
Los condicionales de tipo switch nos ayudan a controlar el flujo de nuestros scritps dada una serie de opciones que sabemos que no van a cambiar, en bash se le conoce como case.

### Sintaxis básica de switch 
```bash
case "$variable" in
	patron1)
		# Comandos
		;;
	patron2)
		# Comandos
		;;
	*)
		# Caso por defecto
		;;
esac
```


```bash
#!/bin/bash
echo "1 - Arch"
echo "2 - Ubuntu"
echo "3 - Fedora"
echo "4 - Debian"
echo "5 - Mint"

read -p "Elige alguna de las distribuciones mencionadas: " distro

case $distro in
	1) echo "Bienvenido a arch";;
	2) echo "Bienvenido a Ubuntu";;
	3) echo "Bienvenido a Fedora";;
	4) echo "Bienvenod a Debian";;
	5) echo "Bienvenido a Mint";;
esac

```

### Ejemplos de case 
Pide al usuario un numero del 1 al 7 y usa case para imprimir el nombre del dia correspondiente.
```bash
Inicio
	Pedir al usuario un numero del 1 al 7
	variable eleccion_usuario
	Segun eleccion_usuario:
		1:
			Mostrar mensaje "Lunes"
		2:
			Mostrar mensaje "Martes"
		3: 
			Mostrar mensaje "Miercoles"
		4. 
			Mostrar mensaje "Jueves"
		5.
			Mostrar mensaje "Viernes"
		6.
			Mostrar mensaje "Sabado"
		7.
			Mostrar mensaje "Domingo"
		De otro modo:
			Mostrar mensaje "Numero invalido"
	FinSegun
Fin
```

```bash
#!/bin/bash
read -p "Elige un numero del 1 al 7: " eleccion_usuario

case $eleccion_usuario in
	1) echo "Lunes";;
	2) echo "Martes";;
	3) echo "Miercoles";;
	4) echo "Jueves";;
	5) echo "Vienres";;
	6) echo "Sabado";;
	7) echo "Domingo";;
	*) echo "Numero invalido";;
esac
```

### Notas Relacionadas
[[Switch Case]]


