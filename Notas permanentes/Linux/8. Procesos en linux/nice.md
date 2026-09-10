Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
Comando encargado de asignar prioridad de uso en CPU a los procesos en ejecución para ello se vale del siguiente rango numerico

| Valor nice | Prioridad          |
| ---------- | ------------------ |
| -20        | Prioridad mas alta |
| 0          | Valor por defecto  |
| 19         | Prioridad mas baja |

### Cuando usar nice
Cuando hay muchos procesos ejecutándose, el kernel de linux tiene que decidir cual de estos procesos usa el CPU, esa decisión se ve influida por el nice number.

### Sintaxis del comando
```bash
nice -n VALOR comando
```

### Caso de uso del comando
Tenemos un e-comerce que vende productos para mascotas, el sitio web se encuentra alojado en la siguiente ruta.
```bash
/var/www/petcomerce
```

Por motivos de seguridad, tenemos que hacer un respaldo de seguridad del sitio web pero tenemos la siguiente situación.
Mientras el respaldo se genera:
* Los usuarios siguen usando el sitio

Nuestro trabajo como dueños del negocio es priorizar las constantes operaciones del sitio web, para ello nos aseguramos que el servidor priorice antes los procesos relacionados al sitio web antes que los proceso relacionados al backup.
```bash
nice -n19 tar -czf petcomerce_bak.tgz /var/www/petcomerce
```

>Algo importante a aclarar sobre nice es lo siguiente, todos aquellos procesos cuyo nice number conlleve el signo -, necesitan ser ejecutados con el comando sudo, esto es debido a que como estamos incrementando la prioridad de uso en CPU, esto vendría siendo responsabilidad de usuarios administradores.
### Notas Relacionadas
[[comandos-linux]]
[[renice]]

