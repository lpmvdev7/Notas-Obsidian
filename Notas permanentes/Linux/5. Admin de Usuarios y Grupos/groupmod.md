Tipo: Nota permanente
Fecha: 2026-07-22
Referencias:
* Linux.pdf
Temas: #Linux #Comandos #grupos 
### ¿Que hace el comando groupmod?
El comando groupmod sirve para modificar grupos.

### Uso del comando
Para usar el comando tenemos la siguiente sintaxis
```bash
 - Change the group name:
   sudo groupmod [-n|--new-name] new_group group_name

 - Change the group ID:
   sudo groupmod [-g|--gid] new_id group_name
```

### Caso de uso
Un caso de uso que se me ocurre para este comando es cuando queramos cambiarle el nombre a un grupo, ya sea porque nos equivocamos o por alguna otra razón
```bash
sudo groupmod -n desarrolladores developers
```


### Notas Relacionadas
[[groupadd]]
[[groupdel]]
[[groups]]
[[gpasswd]]
[[comandos-linux]]
