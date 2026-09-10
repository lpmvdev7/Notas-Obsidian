Tipo: Nota permanente
Fecha: 2026-08-04
Referencias:
* Linux.pdf
Temas: #daemons 
### ¿Como administrar servicios con systemctl?
El comando systemctl nos ayuda a administrar los servicios que son controlados por systemd en nuestro computador. Por ejemplo, si tenemos un servidor de base de datos, al instalar el gestor, normalmente este se ejecuta como un servicio de systemd. Gracias a systemctl podemos iniciar el servicio, detenerlo, reiniciarlo, habilitarlo para que arranque automáticamente con el sistema o revisar su estado cuando ocurre algún problema.

### Usos administrativos de systemctl

Ver el estado de un servicio
```
systemctl status docker
```

Iniciar un servicio
```
systemctl start docker
```

Detener un servicio
```
systemctl stop docker
```

Habilitar el inicio automático de un servicio cuando el sistema arranque.
```
systemctl enable docker
```

Deshabilitar el inicio automático de un servicio cuando el sistema arranque.
```
systemctl disable docker
```

Mostrar el contenido del unit file correspondiente a un servicio
```bash
systemctl cat docker
```

Recargar los daemons una vez editamos la unit file de un servicio.
```bash
systemctl daemon-reload
```

Recargar un servicio
```
systemctl reload docker
```

Proteger a un servicio de ser iniciado
```bash
systemctl mask docker
```

Permitir que un servicio pueda ser iniciado
```bash
systemctl unmask docker
```
### Notas Relacionadas
[[unit file]]


