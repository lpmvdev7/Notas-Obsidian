Tipo: Nota permanente
Fecha: 2026-09-04
Temas: #Bash-script 
### ¿Que es?
set es un builtin que sirve para modificar el comportamiento de la shell, es muy importante en bash script debido a que permite hacer que nuestros scripts sean mas seguros, estrictos y predecibles.

Con la ayuda del comando podemos ver las flags que podemos usar en nuestros bash scripts.
```
set --help
```

Por ejemplo la flag -e, corresponde a errexit y su efecto en scripts es el de detenerlos en caso de que ocurra un error.
```bash
#! /bin/bash
set -e
echo "Listando carpeta inexistente....."
ls /ruta/que/no/existe
```

Con set tambien podemos detectar variables no definidas en nuestro script.
```bash
#!/bin/bash
set -u
echo "$nombre"
```

Supongamos que diseñamos un script cuyo flujo es muy complejo, al ejecutarlo nos damos cuenta de un error, seria muy poco optimo revisar linea por linea de nuestro script, para ello usamos la flag -x, la cual nos permite entrar al modo debug.
```bash
#!/bin/bash
echo "------ INICIO DEL SCRIPT ---------"
set -x
nombre="Luis"
echo "Hola $nombre"
mkdir pruebita
rmdir pruebita
echo "--------- FIN DEL SCRIPT -------------"
```

```bash
------ INICIO DEL SCRIPT ---------
+ nombre='#!/bin/bash'
+ echo '------ INICIO DEL SCRIPT ---------'
------ INICIO DEL SCRIPT ---------
+ nombre=Luis
+ echo 'Hola Luis'
Hola Luis
+ mkdir pruebita
+ rmdir pruebita
+ echo '--------- FIN DEL SCRIPT -------------'
--------- FIN DEL SCRIPT -------------
+ echo '--------- FIN DEL SCRIPT -------------'
--------- FIN DEL SCRIPT -------------
```

### Ejemplo de uso
Script que recibe como argumento el nombre de un servicio de systemd y en base a eso crear la siguiente funcionalidad.
* Exigir al usuario que exista el argumento
* Comprobar que el servicio exista
* Obtener su estado
* Mostrar un reporte indicando el nombre del servicio, su estado y su PID.
```bash
#!/bin/bash

set -euo pipefail

# Comprobar argumentos
if [[ $# -eq 0 ]]; then
    echo "Uso: $0 <servicio>"
    exit 1
fi

servicio="$1"

STATUS=""
PID=0

# Comprobar que el servicio existe
if ! systemctl cat "$servicio.service" &>/dev/null; then
    echo "Error: el servicio '$servicio' no existe."
    exit 1
fi

# Obtener estado
STATUS=$(systemctl is-active "$servicio")

# Obtener PID si está activo
if [[ "$STATUS" == "active" ]]; then
    PID=$(systemctl show "$servicio" --property=MainPID --value)
fi

# Reporte
echo "===== DIAGNÓSTICO ====="
echo
echo "Servicio: $servicio"
echo "Estado:   $STATUS"
echo "PID:      $PID"
echo
echo "======================="
```

### Notas Relacionadas
[[comandos-linux]]


