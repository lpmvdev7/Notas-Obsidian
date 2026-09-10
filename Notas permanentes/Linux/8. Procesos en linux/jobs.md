Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace jobs?
El comando jobs nos ayuda a listar aquellos procesos en segundo plano que están ocurriendo en nuestro equipo.
Este comando es muy útil a la hora de administrar procesos ya que nos brinda mucha información sobre los procesos en segundo plano.
* Nos brinda un listado de los procesos en segundo plano
* Nos brinda el PID del proceso.

### Sintaxis de uso
Nada mas tenemos que escribir jobs en la terminal y si nosotros iniciamos procesos background estos se verán reflejados en el listado del comando.
```bash
jobs
```

### Ejemplo de uso
Supongamos que hago un retraso de 100 segundos y mando ese proceso a background
```bash
sleep 100&
```

Utilizando el comando jobs podemos ver nuestro proceso background.
```bash
jobs
[1]+  Ejecutando              sleep 100 &
```

También podemos ver el status del proceso y su id.
```bash
jobs -l
[1]+  7776 Ejecutando              sleep 100 &

```

Conociendo el id del proceso podemos detenerlo mediante **CTRL + Z**

Conociendo el id del proceso podemos matarlo con el comando kill mediante la opción -9
```bash
kill -9 7776
```

### Notas Relacionadas
[[comandos-linux]]
[[kill]]
[[fg]]
[[bg]]
[[disown]]
