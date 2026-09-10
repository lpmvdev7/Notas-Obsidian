Tipo: Nota permanente
Fecha: 2026-09-04
Referencias:
* #Argumentos-bash #Bash-script 
Temas: 
### ¿Para que sirve $\#?
Esta variable especial nos ayuda a verificar el numero de argumentos que recibe un script, es usada por ejemplo para verificar que un script haya recibido la cantidad de argumentos necesaria para funcionar.

Supongamos que tenemos el siguiente script en bash. 
```bash
if [[ $# -ne 1  ]]; then
	echo "Funcionamiento $0 <palabra>"
	exit 1
fi
echo "Hola $1"
```
El script pide solo un argumento para funcionar, en caso de no recibirlo hacemos la comprobación mediante la variable $# mostrando al usuario un ejemplo de como funciona el script que acaba de ejecutar.
```bash
bash script.sh 
Funcionamiento script.sh <palabra>

bash script.sh pablo
Hola pablo
```
### Notas Relacionadas
[[Variable $0]]
[[Variable $@]]
[[Variable $ASTERISCO]]
[[Variable $$]]
[[Variable $!]]
[[Variable $_]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]



