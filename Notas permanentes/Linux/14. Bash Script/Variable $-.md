Tipo: Nota permanente
Fecha: 2026-09-04
Referencias:
* 
Temas: #Bash-script #Variable-especiales 
### ¿Que hace?
Esta variable especial contiene las opciones activas en la shell actual.
```bash
echo $-
# himBHs
```

Cada letra representa una opción activa en la shell

| Flag | Nombre de la opcion | Descripcion                                                                   |
| ---- | ------------------- | ----------------------------------------------------------------------------- |
| h    | hashall             | Bash memoriza la ubicacion de los comandos para no buscarlos cada vez en PATH |
| i    | interactive         | La sesión es interactiva, es decir que el usuario puede ingresar comandos.    |
| m    | monitor             | El control de jobs esta activo.                                               |
| B    | braceexpand         | La expansion de llaves esta activa                                            |
| H    | histexpand          | La expansion de historial esta activa.                                        |
| s    | stdin               | El shell puede leer los comandos desde la entrada standar                     |
Si queremos ver todas las opciones activas en la shell ejecutamos el siguiente comando:
```bash
set -o
```

### Ejemplo 
A continuación tenemos un ejemplo de porque es importante esta variable especial.
En el siguiente script comprobamos si el modo depuración en bash se encuentra activo.
```bash
#!/bin/bash
if [[ $- == *x*]]; then
	echo "Modo depuracion ACTIVADO"
else
	echo "Modo depuracion DESACTIVADO"
fi
```

### Notas Relacionadas
[[set]]


