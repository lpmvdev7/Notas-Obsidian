Tipo: Nota permanente
Fecha: 2026-08-01
Referencias:
* Linux.pdf
Temas: #Autenticacion 
### ¿Que hace el comando?
El comando lastb nos muestra un registro de todos aquellos intentos fallidos de ingreso al sistema. Para esto el comando lee el contenido del archivo **/var/logs/btmp**.

Para ejecutar este comando necesitamos permisos para usar el comando sudo.
```bash
sudo lastb
```

El comando nos muestra una salida como la siguiente
```bash
sudo lastb
[sudo] contraseña para pueblo:
pueblo   ssh:notty    192.168.1.44     Sat Aug  1 16:14 - 16:14  (00:00)

btmp empieza Sat Aug  1 16:14:54 2026
```

### Caso de uso en el mundo real
Este comando puede ser utilizado como métrica a la hora de auditar una red de servidores linux, ya que dependiendo de los requisitos de la empresa cierto numero de intentos fallidos nos puede indicar que la red es vulnerable y existe alguien tratando de entrar a las cuentas de usuario 

### Notas Relacionadas
[[comandos-linux]]
[[last]]
[[sudo]]

