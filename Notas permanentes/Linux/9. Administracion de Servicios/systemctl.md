Tipo: Nota permanente
Fecha: 2026-08-04
Referencias:
* Linux.pdf
Temas: #daemons 
### ¿Que hace el comando?
El comando systemctl interactua directamente con systemd, el cual es el daemon principal que ejecuta todos los servicios necesarios para que el sistema funcione.
Con systemctl podemos iniciar, detener, reiniciar y recargar los servicios del computador entre muchas otras cosas.

### Uso del comando
El comando systemctl tiene una gran variedad de usos.

Ver el estado general
```bash
systemctl status
```

Nos ayuda a listar servicios.
```bash
systemctl --type=service -all
```

```bash
systemctl list-units
```

Listar servicios activos
```bash
systemctl --type=service -all --state=active
```

Listar servicios inactivos
```bash
systemctl --type=service -all --state=inactive
```

Detección de servicios con errores
```bash
systemctl --failed
```

### Notas Relacionadas
[[comandos-linux]]
[[Servicios linux]]
[[Administracion con systemctl]]
[[systemd]]
