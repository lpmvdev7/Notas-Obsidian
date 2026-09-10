Tipo: Nota permanente
Fecha: 2026-09-01
Referencias:
* 
Temas: #Bash-script #Procesos
### ¿Que hace el comando trap?
El comando trap nos permite interceptar señales o eventos dentro de un script de shell y ejecutar una acción cuando estos ocurren, en lugar de dejar que el shell tome la acción por defecto (que es terminar el proceso)
```bash
# Sintaxis basica
trap 'comando_o_funcion' SEÑAL
```

### Usos de trap
Capturar CTRL+C
```bash
#!/bin/bash
trap 'echo "Hasta luego..."; exit 0' SIGINT
```

### Ejemplos
```bash
#!/bin/bash
trap 'echo "Intentaste detener el script"' SIGINT
while [ true ];
do
	echo "Script en ejecuccion"
	sleep 5
done
# OJO: LA UNICA MANERA DE PARAR ESTE SCRIPT ES CON CTRL + Z, jobs -p y kill -9
```
### Notas Relacionadas
[[comandos-linux]]
[[kill]]


