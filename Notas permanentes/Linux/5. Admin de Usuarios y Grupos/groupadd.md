Tipo: Nota permanente
Fecha: 2026-07-22
Referencias:
* Linux.pdf
Temas:  #Linux #grupos 
### ¿Que hace el comando groupadd?
El comando groupadd es el encargado de crear grupos en sistemas linux,
### Como usar groupadd
La sintaxis del comando es la siguiente:
```bash
sudo groupadd grupo
```

### Caso de uso con groupadd
Una empresa de tecnología recién nacida esta definiendo las responsabilidades de negocio, para ello esta dividiendo estas responsabilidades en departamentos, la empresa busca que cada empleado nuevo que entre a la compañía sea asignado al departamento para el que se le contrato, es por ello que buscan una forma de crear esos departamentos dentro del servidor, para que cuando los nuevos empleados lleguen solo tengan que registrarlos al departamento correspondiente.

#### Solución
La solución a esta problemática es utilizar el comando groupadd. Una vez tenemos definida la estructura organizacional de la empresa, podemos traducir esta a grupos.
![[organigrama -  groupadd]]
Una vez tenemos este organigrama podemos crear los grupos usando groupadd.
```bash
groupadd finanzas
groupadd ingenieria 
groupadd rh
groupadd soporte
```
### Notas Relacionadas
[[groupmod]]
[[groupdel]]
[[groups]]
[[gpasswd]]
[[comandos-linux]]
