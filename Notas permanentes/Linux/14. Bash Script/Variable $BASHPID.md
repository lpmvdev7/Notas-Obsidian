Tipo: Nota permanente
Fecha: 2026-09-04
Temas: #Bash-script #Variable-especiales 
### ¿Que hace?
La variable $BASHPID guarda el id de la sesion actual de bash, a diferencia de la variable $\$ que hace en teoria lo mismo, $BASHPID se diferencia debido a que su valor cambie cuando utilizamos subshells en nuestros scripts, mientras que el de $\$ se mantiene inmutable.

```bash
echo "----------- MAIN SHELL --------------"
echo "PID: $$"
echo "PID con BASHPID: $BASHPID"
(
	echo "--------- SUBSHELL--------------"
	echo "PID: $$"
	echo "PID con BASHPID: $BASHPID"
)
```

Esta variable tiene un buen uso para el control de procesos disparados por los scripts creados por nosotros.
### Notas Relacionadas
[[Variable $0]]
[[Variable $GATO]]
[[Variable $@]]
[[Variable $ASTERISCO]]
[[Variable $$]]
[[Variable $!]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]
[[Variables]]
[[Variables de entorno]]



