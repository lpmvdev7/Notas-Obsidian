Tipo: Nota permanente
Fecha: 2026-09-04
Referencias:
* 
Temas: #Variable-especiales #Bash-script #Argumentos-bash  
### ¿Que es?
La variable @, es una variable especial que representa todos los argumentos posicionales que recibió el script, la forma mas común de utilizar esta variable es entre comillas.

Tenemos la siguiente ejecución de script.
```bash
bash script.sh hola mundo bash
```

 Debido a que pasamos tres argumentos, el valor de $@ seria 
```bash
$@ = hola mundo bash
```

### Ejemplo de un pequeño script
Usando la variable $@ es posible crear scripts que reciban comandos como argumentos, esto es una característica muy interesante ya que básicamente nos permite crear CLIs.
```bash
#!/bin/bash
echo "Ejecutando comandos..."
"$@"
```

Al ejecutarlo se vería así.
```bash
bash script.sh ls -l | head -n5

Ejecutando comandos...
total 149888
-rw-rw-r-- 1 pablo pablo        12 sep  3 22:00 archivillo.txt
-rw-rw-r-- 1 pablo pablo      1286 ago 31 14:46 backup_check.sh
-rw-r--r-- 1 root  root        485 feb 16  2026 backup-repos.list
```

El script funciona porque la variable $@ por dentro equivale a:
```bash
ls -l | head -n5
```


### Ejemplo final
El siguiente script recibe como argumento comandos de linux, en caso de no recibir comando alguno el comando mostrara una pequeña ayuda ejemplificando como usar el programa.
```bash
#!/bin/bash

if [[ $# -eq 0 ]]; then
	echo "Usage: $0 <comandos>"
	exit 1
fi
"$@"
```


### Notas Relacionadas
[[Variable $0]]
[[Variable $GATO]]
[[Variable $ASTERISCO]]
[[Variable $$]]
[[Variable $!]]
[[Variable $_]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]


