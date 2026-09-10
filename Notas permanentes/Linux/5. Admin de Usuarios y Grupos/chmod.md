Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-23
Referencias:
* Linux.pdf
Temas: #Archivos #Comandos #Permisos 
### ¿Que es el comando chmod?
El comando chmod es el comando que nos ayuda a cambiar los permisos que tienen los usuarios sobre los archivos o directorios en sistemas linux.

### Métodos de asignación de permisos
El comando chmod nos brinda de dos métodos para asignar permisos:
* El método numérico: consiste en extraer los valores numéricos asignados de r,w y x con el fin de asignar permisos sobre los archivo o directorios
* El método simbólico: consiste en ejecutar atajos que simbolizan los permisos que queremos asignar sobre un archivo o directorio.

### Método numérico
El comando chmod permite varias formas de usarlo, una de las que exploraremos aquí es mediante el uso de números.
Para ello observemos la siguiente imagen
![[permisos-explicacion|1000]]
En la imagen podemos ver que constantemente se repiten, las letras r, w y x.
Estas letras juegan un papel fundamental a la hora de usar **chmod** ya que cada una de estas tiene un valor numérico asignado cuya suma total es 7.
Estos son los valores numéricos de cada letra:
* **r: 4
* **w: 2
* **x: 1**
Tomando en cuenta que los permisos afectan a 3 partes: Owner, Group y Others podemos razonas que el numero máximo a usar junto con chmod es el 777.

#### Ejemplo método numérico.
>Juan, el desarrollador frontend principal de la empresa, es el propietario de un archivo que contiene la configuración de un proyecto web. Como administrador de sistemas, se te ha solicitado configurar los permisos del archivo para que Juan pueda leer y modificar su contenido. Los demás integrantes de su grupo únicamente deberán tener permiso de lectura, mientras que cualquier otro usuario del sistema no deberá tener acceso al archivo.

Con esto en mente, identificamos a los tres involucrados y el resultado esperado:
```bash
1. Owner: rw- = 4+2 = 6 
2. Group: r-- = 4
3. Other: --- = 0

```

El comando a utilizar seria:
```bash
chmod 640 archivo.txt
```

### Método simbólico
El método simbólico de asignación de permisos con chmod, nos ayuda a asignar permisos de una forma mas sencilla que el método numérico.

La sintaxis que debemos tener en mente es la siguiente:
```bash
chmod [quien][operacion][permiso] archivo
```

| quien     | Operacion                               | Permiso |
| --------- | --------------------------------------- | ------- |
| u: Owner  | +: Agregar permiso                      | r       |
| g: Group  | -: Quitar permiso                       | w       |
| o: Others | =: Establecer exactamente esos permisos | x       |
| a: All    |                                         |         |
#### Ejemplo método simbólico
>Maria es la administradora de la base de datos de la empresa y es la propietaria del archivo backup.sql, que contiene un respaldo completo de la base de datos de producción.
>Por motivos de seguridad, el departamento de TI ha establecido las siguientes reglas:
>1. Maria debe leer, modificar y ejecutar el archivo
>2. Los integrantes de su grupo únicamente podrán leer el archivo
>3. Los demás usuarios del sistema podrán leer el archivo, pero no modificarlo ni ejecutarlo.

##### Solución
```bash
chmod u=rwx,g=r,o=r backup.sql
```

### Notas Relacionadas
[[comandos-linux]]
[[chown]]
