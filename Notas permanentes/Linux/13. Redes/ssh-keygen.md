Tipo: Nota permanente
Fecha: 2026-08-12
Referencias:
* 
Temas: 
### ¿Que hace el comando?
Este comando se encarga de crear llaves publicas y llaves privadas ssh, estas llaves son ampliamente utilizadas en la administración de servidores devops.

El uso que yo le doy al comando es el siguiente:
```bash
# Creamos una llave de tipo rsa con 4096 bits y un comentario para identificarla
ssh-keygen -t rsa -b 4096 -C "Llave pablo"
```

Las llaves creada por el comando se guarda en la siguiente ruta:
```bash
cd .ssh/
ls
id_rsa  id_rsa.pub
```




### Notas Relacionadas
[[ssh-copy-id]]
[[ssh]]
[[ssh-keygen]]
[[comandos-linux]]