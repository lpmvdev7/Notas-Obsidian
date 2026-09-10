Tipo: Nota permanente
Fecha: 2026-07-17
Referencias:
* Linux.pdf
Temas: #Linux #OS #Archivos #Variables-entorno #Comandos 
### ¿Que es una sesión en Linux?
Una sesión en linux se puede definir como el periodo en el cual nosotros como usuarios nos encontramos conectados a la terminal para ejecutar nuestras tareas diarias en esta.

### ¿Porque son importantes las sesiones en Linux?
Las sesiones en Linux son muy importantes ya que en estas se guardan datos que en ocasiones como superusuarios queremos que persistan.
Por ejemplo supongamos que cada vez que iniciemos sesión en la terminal queremos que se muestre el mensaje "Hola $USER", que en mi caso seria "Hola Pablo", para hacerlo tendría que encontrar una forma de colocar esa instrucción y que esta se ejecute cada vez que entremos en la terminal, para ello tenemos el archivo .bashrc

### El archivo .bashrc
Este archivo contiene una serie de scripts que la terminal ejecuta cada vez que entramos en ella. Aquí podemos personalizar nuestra terminal colocando mensajes de bienvenida o mas importante aun podemos mantener PERSISTENCIA con las variables de entorno que creamos o modificamos, los alias que creamos entre muchas otras cosas. 
Este archivo es muy importante ya que permite que todas aquellas modificaciones hechas en una sesion anterior vivan por siempre entre todas nuestras futuras sesiones.

### Como funciona el archivo bashrc
1. Abrimos una terminal
2. Se crea un nuevo proceso de Bash
3. Bash lee el archivo .bashrc
4. Bash ejecuta cada instrucción contenida en .bashrc (alias, variables, etc)
5. Se termina de ejecutar y tenemos  una sesión con las configuraciones declaradas en .bashrc


### Notas Relacionadas
[[Variables de entorno]]
[[PATH]]
[[CLI]]
[[Bash Scripting]]
[[Sistema de archivos]]
[[alias]]
[[Vim]]
