Tipo: Nota permanente
Fecha: 2026-08-12
Referencias:
* Linux.pdf
Temas: #Secure-shell #Redes #Linux 
### ¿Que hace el comando?
El comando ssh-copy-id se encarga de copiar una llave publica ssh creada previamente con el comando ssh-keygen hacia un destino remoto. Para usar este comando tenemos que conocer la direccion ip de la computadora a la cual queremos mandar nuestra copia.

La sintaxis de uso del comando es la siguiente.
```bash
# Copiamos la llave publica colocando la ruta de esta
ssh-copy-id -i ~/.ssh/id_rsa.pub pablo@172.18.0.2
```

Con esto hecho el comando nos permite iniciar sesión en una maquina remota sin la necesidad de colocar contraseña.
```bash
ssh pablo@172.18.0.2
```

### ¿Porque funciona el comando?
El comando funciona porque lo que hace es mandar una copia de nuestra llave publica al equipo que nos queremos conectar. El equipo la recibe y la coloca en un archivo llamado authorized_keys ubicado en .ssh, ese archivo guarda todas las llaves publicas que pueden acceder al equipo mediante ssh.
```
cat ~/.ssh/authorized_keys
```
### Notas Relacionadas
[[comandos-linux]]
[[ssh-keygen]]
[[ssh]]
