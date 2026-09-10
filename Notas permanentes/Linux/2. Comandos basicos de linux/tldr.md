Tipo: Nota permanente
Fecha: 2026-07-15
Referencias:
* 
Temas:  #Linux #Comandos #Manuales-ayuda
### ¿Que es tldr?
tldr es un comando que nos sirve como guía con ejemplos para saber que hacer con un determinado comando en linux.
#### Ejemplo de uso
Supongamos que estamos usando ls para listar los elementos de una carpeta y queremos que se nos listen las carpetas ocultas del sistema, es decir aquellas que inician con un ., el comando ls tiene esa opción pero nosotros no sabemos utilizarla, allí es cuando entra tldr.
tldr lo que hace es mostramos mediante ejemplos como es que podemos usar cierto comando.

```bash
tldr ls

ls

Lista los contenidos de directorios.
Más información: https://www.gnu.org/software/coreutils/manual/html_node/ls-invocation.html.

 - Lista un archivo por línea:
   ls -1

 - Lista todos los archivos, incluyendo archivos ocultos:
   ls [-a|--all]

 - Lista todos los archivos, añadiendo / al final de los nombres de directorios:
   ls [-F|--classify]

 - Lista todos los archivos en formato largo (permisos, propietarios, tamaño y fecha de última modificación):
   ls [-la|--all -l]

 - Lista en formato largo y tamaño legible por humanos (i.e., KiB, MiB, GiB, etc.):
   ls [-lh|-l --human-readable]

 - Lista recursivamente en formato largo y ordena los tamaños de mayor a menor:
   ls -lSR|-lS --recursive

 - Lista todos los archivos en formato largo y ordenados por fecha de modificación (archivos más viejos en primer lugar):
   ls [-ltr|-lt --reverse]

 - Lista solamente directorios:
   ls [-d|--directory] */

```
### Notas Relacionadas
[[comandos-linux]]
[[man]]

