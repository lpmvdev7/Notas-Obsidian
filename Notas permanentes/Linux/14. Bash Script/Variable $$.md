Tipo: Nota permanente
Fecha: 2026-09-04
Temas:
* #Variable-especiales #Bash-script  
### ¿Que hace?
La variable especial \$$ guarda el proccess id del shell actual, es decir que guarda el numero exacto del proceso que esta ejecutando nuestro script.

```bash
#!/bin/bash
if [[ $# -eq 0]]; then
	echo "Usage: $0 <comando>"
fi

"$@"
echo "El comando ejecutado con $0 fue: $*"

# Imprimimos el PID del script
echo "EL PID es $$"
```

```bash
#!/bin/bash
echo "El PID ES: $$"
sleep 10
```
### Notas Relacionadas
[[Variable $0]]
[[Variable $GATO]]
[[Variable $@]]
[[Variable $ASTERISCO]]
[[Variable $!]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]


