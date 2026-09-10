Tipo: Nota permanente
Fecha: 2026-07-20
Referencias:
* Linux.pdf
Temas:  #Linux #Archivos #Comandos #Flujos-estandar 
### ¿Que es el redireccionamiento?
El redireccionamiento en linux es la manipulación de los flujos estándar llámense: stdin, stdout y stderr para enviarlos a destinos diferentes como podrían ser archivos.
Esto tiene gran variedad de usos como auditorias o la traza de errores.

### Operador > 
El operador > nos va ayudar a redireccionar salidas hacia archivos, lo que hace es sobrescribir completamente el archivo de destino.

```bash
echo "Redireccionando este texto" > archivo.txt
cat archivo.txt
```

### Operador >>
En algunas ocasiones no querremos sobrescribir el contenido de todo un archivo de texto, en ocasiones únicamente querremos agregar una nueva linea al archivo de texto, para esos casos tenemos el operador **>>** 

```bash
echo "Nueva linea de texto" >> archivo.txt
cat archivo.txt
```

### Operador ;
En caso de que queramos concatenar la ejecucion de varios comandos  de forma seguida podemos usar el operador **;** 
Este operador hace que el siguiente comando se ejecute sin importar si el otro ha tenido exito en su ejecución o no.
```bash
echo "Nuevo archivo" > new.txt; mkdir newc; cd newc; pwd
/home/pablo/Escritorio/Estudio/linux/newc
```
### Notas Relacionadas
[[Flujos estandar en Linux]]


