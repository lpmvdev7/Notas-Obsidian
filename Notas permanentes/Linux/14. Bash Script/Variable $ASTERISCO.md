Tipo: Nota permanente
Fecha: 2026-09-04
Referencias:
* 
Temas: #Bash-script #Variable-especiales 
### ¿Que hace?
La variable especial $* guarda todos los argumentos que recibe un script en una única cadena de texto. Por lo general se usa entre comillas.

### Ejemplo
En este pequeño ejemplo utilizamos la variable $* de forma que el usuario sepa que el comando mandado como argumento se ejecuto.
```bash
#!/bin/bash
if [[ $# -eq 0]]; then
	echo "Usage: $0 <comando>"
fi

"$@"
echo "El comando ejecutado con $0 fue: $*"
```

El principal uso que se le puede dar a esta variable es como un registro de aquellos argumentos que el usuario pasa a un script.

### Notas Relacionadas
[[Variable $0]]
[[Variable $GATO]]
[[Variable $@]]
[[Variable $$]]
[[Variable $!]]
[[Variable $_]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]


