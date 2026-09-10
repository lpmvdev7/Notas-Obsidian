Tipo: Nota permanente
Fecha: 2026-07-17
Referencias:
* Linux.pdf
Temas: #Comandos #Linux #pipes #Operadores-logicos
### Los operadores lógicos en la terminal
La terminal de linux nos permite realizar muchas tareas, para ello nos provee de varias funcionalidades que como ingenieros en software nos ayudan a realizar nuestras tareas eficientemente. Una de estas funcionalidades es el uso de operadores lógicos en la terminal

#### AND
El operador booleano AND regresa TRUE solo si ambos valores son TRUE, en caso contrario siempre sera FALSE.
>**Ejemplo 1**
>En este ejemplo podemos ver el uso del operador AND, creamos una carpeta y despues imprimos un mensaje en consola, como es la primera ejecuccion de esta instruccion en la terminal, esta resultara tal y como en el ejemplo mostrado aqui abajo. 

```bash
mkdir carpetita && echo "La carpeta se ha creado wiii"
La carpeta se ha creado wiii
```

>pero si la volvemos a ejecutar esta instruccion lo que sucedera es que la parte de la creacion de la carpeta pasara a ser false ya que el comando no se ejecutara debido a la existencia de una carpeta con ese mismo nombre, es decir seria un caso de FALSE AND TRUE dando FALSE.

```bash
mkdir carpetita && echo "La carpeta se ha creado wiii"
mkdir: no se puede crear el directorio «carpetita»: El archivo ya existe
```
#### OR
El operador booleano OR regresa TRUE solo si alguno de los valores es TRUE, en caso de que ambos valores sean FALSE regresa FALSE.

>**Ejemplo 1**
>Para este ejemplo daremos por hecho que en nuestro espacio de trabajo existe una carpeta llamada "carpetita", la cual servirá como nuestro valor TRUE, para nuestro valor FALSE estaremos tratando de ejecutar el comando cat a un archivo inexistente.

```bash
ls carpetita/ || cat archivo.txt
```


### Notas Relacionadas
[[Flujos estandar en Linux]]
[[comandos-linux]]
[[Bash Scripting]]
[[Pipelines]]
[[Algebra de Bool]]
[[Condicionales]]

