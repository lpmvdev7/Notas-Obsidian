Tipo: Nota permanente
Fecha: 2026-08-05
Referencias:
* Linux.pdf
Temas: #Paquetes-linux 
### ¿Que hace el comando?
Comando perteneciente a distribuciones linux basadas en Debian como Ubuntu y Linux MInt cuyas funciones nos permiten la manipulación de paquetes en nuestro sistema.

### Usos del comando apt

Actualizar la lista de paquetes
```bash
sudo apt update
```

Actualizar los paquetes instalados
```bash
sudo apt upgrade
```

Ver aquellos paquetes que pueden ser actualizados
```bash
apt list --upgradable
```

Buscar un paquete
```bash
apt search htop
```

Instalar un paquete
```bash
sudo apt install htop
```

Eliminar un paquete
```bash
sudo apt remove htop
```

Eliminar todos los archivos relacionados a un paquete en nuestro sistema
```bash
sudo apt purge htop
```

Listar los paquetes instalados 
```bash
apt list --installed
```

Limpiar el computador de aquellos paquetes obsoletos
```bash
sudo apt autoremove
```

Ver la información de un paquete en especifico
```bash
sudo apt show python3
```

Hacer una actualización completa del sistema, no solo de los paquetes
```bash
sudo apt full-upgrade
```


### Notas Relacionadas
[[comandos-linux]]
[[sudo]]
[[Gestor de paquetes]]
[[Paquete]]
[[Repositorio de paquetes]]
