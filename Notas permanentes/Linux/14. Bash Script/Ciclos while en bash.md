Tipo: Nota permanente
Fecha: 2026-09-01
Referencias:
* 
Temas: 
### ¿Para que sirve?
El ciclo while es una estructura de control del tipo iterativa que nos permite ejecutar un bloque de código dependiendo de si se cumple o no una condición.

En bash el ciclo while se escribe de la siguiente manera:
```bash
while [ condicion ]
do
	# Comandos
done

while [[ condicion ]]; do
	# Comandos
done
```

### Ejemplos
Usar un while para imprimir los números del 1 al 10
```bash
#!/bin/bash
contador=10
while [ $contador -gt 0 ]
do
        echo "$contador"
        ((contador--))
done
```

Contador descendente dependiendo del numero que me de el usuario.
```bash
#!/bin/bash
read -p "Coloca un numero: " numero_usuario
while [ $numero_usuario -gt 0 ]
do
        echo "$numero_usuario"
        ((numero_usuario--))
done
```

Mediante un while sumar los números del 1 al 100, mostrando el resultado total al final.
```bash
#!/bin/bash
suma=0
iteracion=100

while [ $iteracion -gt 0 ]
do
        ((suma+=iteracion))
        ((iteracion--))
done
echo "$suma"
```

Mediante un script revisa lo siguiente:
1. Cada 5 segundos, revise el porcentaje de uso del disco de la partición raiz (/)
2. Si el uso es menor al 80% imprime un mensaje indicando que todo esta en orden
3. Si el uso es mayor al 80% o mas, imprime un mensaje de advertencia.
```bash
#!/bin/bash
trap 'echo "Monitor detenido."; exit 0' SIGINT
while true
do
	porcentaje=$(df -h / | tail -n +2 | awk '{ sub("%", "", $5); print $5 }')
	if [[ $porcentaje -lt 80 ]]; then
		echo "Todo esta en orden: $porcentaje%"
	elif [[ $porcentaje -ge 80 ]]; then
		echo "Cuidado con el uso: $porcentaje%"
	fi
	sleep 5
done
```
### Notas Relacionadas
[[Ciclo while]]
[[Comando trap]]


