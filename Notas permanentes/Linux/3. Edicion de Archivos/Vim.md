Tipo: Nota permanente
Fecha: 2026-07-15
Referencias:
* Linux.pdf
Temas: #Archivos #Linux #Vim
### ¿Que es Vim?
Vim es un editor de texto para la terminal de comandos de sistemas basados en unix, aplicando a estos las distribuciones de linux como Ubuntu, Fedora, ArchLinux y Linux Mint.

### Primeros pasos con vim
Si queremos crear un archivos de texto lo podemos hacer con el comando vim, esto nos abrira un editor de texto.

```bash 
vim archivo.txt
```

#### Modos en Vim
Cuando estamos trabajando con Vim nos podemos encontrar con dos modos de trabajo:
1. Modo normal: El modo normal es aquel que nos permite ejecutar comandos en VIM pero que no nos permite editar el contenido de nuestro archivo. Este se encuentra activo por defecto cuando entramos a nuestros archivos.
2. Modo inserción: El modo inserción es aquel que nos permite editar nuestro archivo libremente. Se activa cuando presionamos la tecla **i** y para desactivarlo presionamos **ESC**

##### Comandos Modo Insercion
| Comando       | Uso                                                 |
| ------------- | --------------------------------------------------- |
| i             | Entrar en el modo de insercion en vim               |
| ESC           | Salir del modo de insercion en vim                  |
| a             | Insertar un caracter despues del cursor             |
| o (minuscula) | Insertar un nuevo parrafo despues del actual        |
| O (mayuscula) | Insertar un nuevo parrafo antes del parrafo actual. |
##### Comandos Modo Normal
| Comando                | Uso                                                                               |
| ---------------------- | --------------------------------------------------------------------------------- |
| 0                      | Nos vamos al inicio de una linea de texto                                         |
| $                      | Ir al final de una linea de texto                                                 |
| yy                     | Copiar la linea actual                                                            |
| p (minuscula)          | Copiar despues de la linea actual                                                 |
| P (mayuscula)          | Copiar antes de la linea actual                                                   |
| u                      | deshacer                                                                          |
| CTRL + R               | rehacer                                                                           |
| :w                     | Guardar un archivo                                                                |
| :wq                    | Guardar y salir                                                                   |
| :q!                    | Salir sin guardar                                                                 |
| N**comando**           | N significa el numero de veces que queremos repetir un comando                    |
| NG                     | Nos ayuda a dirigirnos a una linea de texto colocando el numero de esta           |
| gg                     | Comando para dirigirnos al inicio del archivo                                     |
| G                      | Nos movemos al final del archivo                                                  |
| w                      | ir al inicio de la palabra siguiente                                              |
| e                      | ir al final de una palabra                                                        |
| *                      | Encontrar todas las apariciones de la palabra que se encuentra sobre el cursor    |
| g_                     | Nos dirige al ultimo caracter de una linea de texto                               |
| f**letra**             | Nos lleva a la siguiente ocurrencia de una letra especifica                       |
| F                      | Retrocede para llevarnos a la anterior ocurrencia de un caracter                  |
| CTRL + P               | Autocompletado que se basa en las palabras que ya estan en el texto.              |
| V                      | Seleccionamos los caracteres, esto nos podria ayudar para borrar elementos.       |
| :split                 | Dividimos la pantalla en dos de manera horizontal.                                |
| CTRL + W               | Nos cambia de pantalla dividida para que podamos empezar a editar el archivo.     |
| :vsplit                | Dividimos la pantalla en dos de manera vertical                                   |
| :split **archivo.txt** | Creamos una vista dividida con el archivo actual y el archivo que especifiquemos. |
| /palabra               | Encontrar una palabra                                                             |
| :terminal              | Dividimos la pantalla abriendo una terminal mientras trabajamos en vim.           |

### Notas Relacionadas
[[Notas permanentes/Linux/3. Edicion de Archivos/About - Edicion de archivos]]

