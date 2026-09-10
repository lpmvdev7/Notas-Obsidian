Tipo: Nota permanente
Fecha: 2026-09-02
Referencias:
* 
Temas: 
### ¿Que son los arrays asociativos en bash?
Los arrays asociativos son estructuras que nos permiten guardar datos mediante pares clave-valor 

### ¿Cual es la principal diferencia entre arrays asociativos y arrays indexados en bash?
La principal diferencia es la forma en la que accedemos a los datos en ambos, con los arrays indexados como lo dice su nombre, accedemos mediante su indice, mientras que con los arrays asociativos accedemos a un valor mediante su llave.

### Como se utilizan los arrays asociativos
Los array asociativos se declaran de la siguiente manera:
```bash
declare -A usuario
```

Después de declararlos le podemos asignar valores.
```bash
usuario[nombre]="Luis"
usuario[edad]=24
usuario[lenguaje]="Bash"
usuario[rol]="DevOps"
```

Así accedemos a los valores.
```bash
echo "${usuario[nombre]}"
echo "${usuario[edad]}"
echo "${usuario[lenguaje]}"
```

Si lo que queremos es acceder a todos los valores de un array asociativo en bash usamos la siguiente sintaxis.
```bash
echo "${usuario[@]}"
```

Pero si lo que queremos es acceder a las claves de un array asociativo usamos la siguiente sintaxis.
```bash
echo "${!usuario[@]}"
```

De la siguiente manera podemos averiguar cuantos elementos tiene un arreglo asociativos.
```bash
echo "${#usuario[@]}"
```

Comprobar si existe una clave
```bash
if [[ -v "usuario[rol]" ]]; then
	echo "El usuario cuenta con clave rol"
else
	echo "El usuario no cuenta con una clave llamada rol"
fi
```

Eliminar un elemento
```bash
unset 'usuario[rol]'
```

### Ejemplo
Un script que administre la información de varios servidores utilizando un array asociativo (diccionario), los servidores son los siguientes:
* web01
* web02
* db01
* db02
* dns01
Cada servidor tendrá asociado alguno de estos estados:
* online
* offline
* maintenance
Se debe mostrar un reporte con los servidores al lado de su estado y contar cuantos servidores están en cada estado.
```bash
#!/bin/bash
online_count=0
offline_count=0
maintenance_count=0
declare -A servidores

servidores[web01]="online"
servidores[web02]="offline"
servidores[db01]="maintenance"
servidores[db02]="online"
servidores[dns01]="offline"

for servidor in "${!servidores[@]}"
do
	echo "$servidor: ${servidores[$servidor]}"
	if [[ "${servidores[$servidor]}" == "online" ]]; then
		((online_count++))
	elif [[ "${servidores[$servidor]}" == "offline" ]]; then
		((offline_count++))
	else
		((maintenance_count++))
	fi
done
echo "--- RESUMEN ---"
echo "Servidores online: $online_count"
echo "Servidores offline: $offline_count"
echo "Servidores en mantenimiento: $maintenance_count"
```

### Notas Relacionadas
[[Arrays en bash]]


