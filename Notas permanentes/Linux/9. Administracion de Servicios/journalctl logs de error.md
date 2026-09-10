Tipo: Nota permanente
Fecha: 2026-08-05
Referencias:
* Linux.pdf
Temas: #logs 
### ¿Como se utiliza journalctl para encontrar logs de errores?
journalctl es un comando que nos ayuda a ver y manipular aquellos logs generados por el daemon journald, entre estos logs se encuentran errores.

### Niveles de prioridad
Los niveles de prioridad en journalctl es un rango de números que va del 0 al 7, este rango representa los niveles de severidad de un log.

| Prioridad | Codigo  |
| --------- | ------- |
| 0         | emerg   |
| 1         | alert   |
| 2         | crit    |
| 3         | err     |
| 4         | warning |
| 5         | notice  |
| 6         | info    |
| 7         | debug   |
Con estos códigos podemos encontrar logs que sean emergencias, alertas, críticos, errores, advertencias, notificaciones, informativos y debugs.
Para ello tenemos la opción -p la cual nos permite usar los números de prioridad y así encontrar un log perteneciente a las categorías anteriormente mencionadas.

```bash
# Encontrar todos los errores en el sistema
journalctl -p3
```

```bash
# Encontrar todos los errores en el servicio docker
journalctl -u docker.service -p3
```

```bash
# Encontrar todos los errores del sistema y que me den una descripcion de estos
journalctl -p3 -xe
```
### Notas Relacionadas
[[comandos-linux]]
[[journald]]
[[journalctl]]
[[Servicios linux]]



