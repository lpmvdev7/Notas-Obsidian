Tipo: Nota permanente
Fecha: 2026-08-28
Referencias:
* Linux.pdf
Temas: #Bash-script #Subshells
### ¿Que son las subshells?
Una subshell es una shell que nace a partir de un proceso iniciado por otra, es decir que es una nueva instancia que se crea desde otro shell para ejecutar comandos de forma aislada.
Cuando creamos una subshell en linux lo que estamos haciendo es crear un entorno aislado en el cual se ejecutan comandos, es como ejecutar comandos de forma asíncrona mientras nuestro proceso principal se sigue ejecutando.

En este ejemplo creamos una subshell mediante paréntesis, notese que el resultado de la subshell no tiene efecto en la shell principal.
```bash
nombre="Luis"
(
	nombre="Pedro"
	echo "$nombre"
)
echo "$nombre"

# Resultado
# Pedro
# Luis
```

En este otro ejemplo creamos una subshell que si captura el resultado hacia la shell principal, esto mediante el uso de $.
```bash
resultado=$(echo "Hola")
echo "$resultado"
```

### Ejercicio
Crear un bash script que haga lo siguiente:
* Guarde dentro de una variable el directorio actual.
* Utilice un subshell con ( ) para:
	* Entrar a /tmp
	* Mostrar el directorio actual
* Después que se termine de ejecutar la subshell, mostrar nuevamente el directorio actual
* Por ultimo utilizar $() para guardar en una variable la cantidad de archivos que existen en /tmp
```bash
#! /bin/bash

current_directory=$(pwd)
(
	cd /tmp
	pwd
)
echo "$current_directory"
archivos_tmp=$(cd /tmp && ls | wc -l)
echo "$archivos_tmp"
```

```bash
bash subshellscript.sh 
/tmp
/home/pablo
16
```
### Notas Relacionadas
[[Bash Scripting]]
[[Comando bash y sh]]


