Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-22
Referencias:
* 
Temas:  #Linux #grupos #Comandos 
### ¿Que hace el comando gpasswd?
El comando gpasswd es un comando que nos ayuda a administrar grupos. 
Este comando tiene poderes administrativos en los archivos /etc/groups y /etc/gshadow por lo que es ampliamente usado para tareas administrativas relacionadas a grupos de usuarios.

### Uso
A continuación se muestran algunos de los diferentes usos que se le puede dar al comando gpasswd.
```bash
 - Define group administrators:
   sudo gpasswd [-A|--administrators] user1,user2 group

 - Set the list of group members:
   sudo gpasswd [-M|--members] user1,user2 group

 - Create a password for the named group:
   gpasswd group

 - Add a user to the named group:
   gpasswd [-a|--add] user group

 - Remove a user from the named group:
   gpasswd [-d|--delete] user group

```

### El archivo /etc/gshadow
Menciono este archivo ya que nos va a servir como ayuda en algunas ocasiones cuando ejecutemos instrucciones con gpasswd.
Esto es debido a que este archivo muestra información de los grupos como los administradores y sus miembros usando la siguiente sintaxis.
```bash
grupo:contraseña:administradores:miembros
```

### Caso de uso real para el comando gpasswd 
En una empresa dedicada a la infraestructura de nube, el administrador de servidores se ha dado cuenta que dedica mucho tiempo a agregar usuarios, eliminarlos de grupos pertenecientes a 2 departamentos clave de la empresa: ingeniería y experiencia de usuario, dado la creciente entrada de personal, el administrador de servidores tomo la decisión de delegar la administración de los grupos a los respectivos jefes de esas divisiones. 
**¿Que es lo que tiene que hacer el administrador de servidores para otorgar estos permisos?**

#### Solución
Viendo la descripción del problema se me ocurre una solución. El administrador del sistema tiene que agregar a los responsables directos de esas áreas como administradores de sus respectivos grupos.
```bash

sudo gpasswd -A luis ingenieria
sudo gpasswd -A maria ux

```

Una vez que ambos responsables de área entren en sus respectivos perfiles se podrán dar cuenta que ahora podrán agregar y eliminar usuarios de sus respectivos grupos.
```bash
gpasswd -a juan ingenieria
gpasswd -d juan ingenieria
```
### Notas Relacionadas
[[groupadd]]
[[groups]]
[[groupmod]]
[[Grupos]]
[[comandos-linux]]



