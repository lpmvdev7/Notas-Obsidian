Tipo: Nota permanente
Fecha: 2026-09-03
Temas:
* #Variables #Variable-especiales #Bash-script 
### ¿Que son las variables especiales en bash?
Las variables especiales permiten que nuestros scripts interactuen con argumentos, procesos, archivos, señales y con su propio entorno de ejecución.

| Variable especial | Significado                                                                                   |
| ----------------- | --------------------------------------------------------------------------------------------- |
| $0                | Nombre o ruta con el que fue invocado el script o shell                                       |
| $#                | Cantidad de argumentos posicionales recibidos por el script                                   |
| "$@"              | Expande todos los argumentos posicionales como palabras separadas (cada uno respeta comillas) |
| "$*"              | Expande todos los argumentos posicionales como una sola cadena unida.                         |
| \$$               | PID del shell actual                                                                          |
| $!                | PID del ultimo proceso proceso en background                                                  |
| $-                | Opciones (flags) activas del shell                                                            |
| $PIPESTATUS       | Exit codes de los comandos ejecutados en el ultimo pipeline                                   |
| $BASHPID          | PID del proceso BASH actual, se vuelve util en subshells.                                     |
### Notas Relacionadas
[[Variable $0]]
[[Variable $GATO]]
[[Variable $@]]
[[Variable $ASTERISCO]]
[[Variable $$]]
[[Variable $!]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]
[[Variables]]
[[Variables de entorno]]



