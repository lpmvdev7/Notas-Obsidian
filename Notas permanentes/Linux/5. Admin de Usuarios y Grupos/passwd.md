Tipo: Nota permanente
Fecha: 2026-07-22
Referencias:
* Linux.pdf
Temas:  #Comandos #usuarios 
### ¿Que hace el comando passwd?
El comando passwd se utiliza junto con useradd para asignarle al nuevo usuario que estamos creando una contraseña. Esta contraseña se almacena como un hash en el archivo **/etc/shadow**

### ¿Como usar el comando passwd?
El comando passwd por lo general lo vamos a utilizar al momento de usar useradd.
```bash
sudo useradd pablo && passwd
```

Para cambiar la contraseña de un usuario
```bash
sudo passwd pablo
```

### Sobre el archivo /etc/shadow
En este archivo se almacenan las contraseñas de los usuarios del sistema, estas contraseñas nada mas pueden ser visibles para aquellos usuarios con capacidades root. Al abrir el archivo lo que verán sera una lista de contraseñas hasheadas.

```bash
cat shadow
root:*:20374:0:99999:7:::
daemon:*:20374:0:99999:7:::
bin:*:20374:0:99999:7:::
sys:*:20374:0:99999:7:::
sync:*:20374:0:99999:7:::
games:*:20374:0:99999:7:::
man:*:20374:0:99999:7:::
lp:*:20374:0:99999:7:::
mail:*:20374:0:99999:7:::
news:*:20374:0:99999:7:::
uucp:*:20374:0:99999:7:::
proxy:*:20374:0:99999:7:::
www-data:*:20374:0:99999:7:::
backup:*:20374:0:99999:7:::
list:*:20374:0:99999:7:::
irc:*:20374:0:99999:7:::
_apt:*:20374:0:99999:7:::
nobody:*:20374:0:99999:7:::
ubuntu:!:20374:0:99999:7:::
```

### Ejemplo de passwd
Una empresa de logística le pide al departamento de TI añadir para todos los usuarios una contraseña, esto con fines de mejorar la seguridad

#### Solucion
El departamento de TI puede agregar lo siguiente:
```bash
passwd usuario
```

### Notas Relacionadas
[[comandos-linux]]
[[Usuarios]]
[[usermod]]
[[userdel]]
[[useradd]]
