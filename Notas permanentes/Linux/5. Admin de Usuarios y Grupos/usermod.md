Tipo: Nota permanente
Fecha: 2026-07-22
Referencias:
* Linux.pdf
Temas: #Linux #Comandos #usuarios 
### ¿Que hace el comando usermod?
El comando usermod se encarga de modificar un usuario existente.

### Uso del comando
La sintaxis de uso del comando cambia dependiendo de lo que querramos hacer con este, este es un comando que se nutre de las opciones de modificacion que brinda.
```bash
 - Cambia el nombre de un usuario:
   sudo usermod [-l|--login] nuevo_nombre usuario

 - Cambia el ID de un usuario:
   sudo usermod [-u|--uid] id usuario

 - Cambia la interfaz de comandos (shell) a un usuario:
   sudo usermod [-s|--shell] ruta/a/interfaz_comando usuario

 - Añade un usuario a grupos suplementarios (ten en cuenta los espacios en blanco):
   sudo usermod [-a|--append] [-G|--groups] grupo1,grupo2 usuario

 - Cambia el directorio home de un usuario:
   sudo usermod [-m|--move-home] [-d|--home] ruta/al/nuevo_home usuario
```

### Caso de uso con usermod
El departamento de TI de una empresa cometió un error a la hora de asignarle un grupo a laura, laura es una desarrolladora full-stack y trabaja con el equipo de ingeniera, el problema es que laura noto que no puede acceder a los archivos del equipo de ingeniería, laura se dio cuenta de que el administrador de TI había cometido un error, la habia colocado en el equipo de contaduría en lugar del equipo de ingeniería, mas pronto que tarde laura comunica este error al departamento de TI.  ¿Como solucionarías este error?
### Solución
Como administrador de TI utilizaría el comando usermod, con el objetivo de reasignar a laura en el departamento de ingeniería.
```bash
usermod -aG ingenieria laura 
```
Con este comandos, nos aseguramos que laura pertenezca al equipo de ingeniería.

### Notas Relacionadas
[[Usuarios]]
[[Grupos]]
[[comandos-linux]]
[[userdel]]
[[useradd]]
[[usermod]]
[[who]]
[[passwd]]
