Tipo: Nota permanente
Fecha: 2026-07-16
Referencias:
* Linux.pdf
Temas:  #Variables-entorno
### ¿Que son las variables de entorno?
Las variables de entorno son configuraciones previas del sistema que prevalecen entre sesiones, siendo un ejemplo de sesion cuando abres la terminal.
Una variable de entorno afecta el comportamiento de los comandos y de los ejecutables del sistema, ya que muchas de ellas hacen referencia a valores que se encuentran en el sistema, como es el caso de PATH.

Para poder ver las variables de entorno del sistema podemos correr el siguiente comando:
```bash
env
```
El comando nos muestra todas aquellas variables de entorno de nuestro sistema.

Otro comando con el que contamos para poder ver nuestras variables de entorno es el comando
```bash
printenv
```

### ¿Como se que hacen esas variables de entorno?
Los comandos que mencione anteriormente funcionan unicamente para imprimir los valores clave-valor de nuestras variables de entorno pero en si, no nos ayudan a comprender que es lo que hacen estas y su impacto en el sistema.
Para ello ejecutamos el siguiente comando:
```bash
man environ
```
Si bien no contiene todas las variables de entorno si contiene algunas de las mas importantes como:
$HOME, $PWD y $PATH

### Podemos crear variables de entorno?
La respuesta es SI y de hecho es algo que deberíamos practicar ya que el uso de variables de entorno es algo que se ve mucho en scripts o si queremos hacernos la vida mas fácil utilizando la terminal.

#### Ejemplo de una variable de entorno creada por mi
Actualmente tengo un directorio de trabajo para mis proyectos, el problema aquí es que cada que quiero entrar a este tengo que ejecutar el comando cd en repetidas ocasiones para poder entrar a mi directorio de trabajo.
```bash
pwd
/home/pablo/Escritorio/Proyectos
```

Una solución que se me ocurre para este problema es crear una variable de entorno que apunte directamente a la ruta de mi directorio de trabajo.
```bash
export PROYECTOS_DIR=/home/pablo/Escritorio/Proyectos
```

Ahora puedo navegar hacia ese directorio utilizando cd una sola vez.
```bash
cd $PROYECTOS_DIR
```

Pero esto no acaba aquí, incluso puedo crear un alias que me lleve directamente a esa carpeta.
```bash
alias proyectos="cd $PROYECTOS_DIR"
proyectos
pwd
/home/pablo/Escritorio/Proyectos
```

Si bien este es uno uso muy básico de las variables de entorno, creo que sirve como un muy buen ejemplo de todas las posibilidades de personalización que nos brindan estas a la hora de trabajar en entornos Linux

### Las variables de entorno persisten entre sesiones?
Depende de como queramos que sea y de los objetivos que tengamos al trabajar con variables de entorno, si queremos que NO persistan las declaramos tal cual los ejemplos de arriba, si queremos que SI persitan las declaramos en un archivo llamado .bashrc.

### Notas Relacionadas
[[man]]
[[PATH]]
[[Bash Scripting]]
[[alias]]
[[Sesiones linux]]
