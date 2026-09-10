Tipo: Nota permanente
Fecha: 2026-09-03
Referencias:
* 
Temas: #Bash-script #Argumentos-bash 
### ¿Que es?
La variable $0 nos muestra la ruta desde la cual se ha ejecutado nuestro bash script.

```bash
#!/bin/bash
echo "$0"
```

### Ejemplo
En este script detectamos si fue ejecutado desde una ruta absoluta, una ruta relativa o solo usando el nombre del script.
```bash
#!/bin/bash

echo "Nombre de ejecución: $0"

if [[ "$0" == /* ]]; then
    echo "Tipo de ruta: absoluta"
elif [[ "$0" == */* ]]; then
    echo "Tipo de ruta: relativa"
else
    echo "Tipo de ruta: solamente nombre"
fi

echo
echo "Puedes volver a ejecutar el script utilizando:"
echo "$0"
```

### Notas Relacionadas
[[Variable $GATO]]
[[Variable $@]]
[[Variable $ASTERISCO]]
[[Variable $$]]
[[Variable $!]]
[[Variable $_]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]


