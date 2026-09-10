Tipo: Nota permanente
Fecha: 2026-07-24
Referencias:
* Linux.pdf
Temas: #Linux #Archivos #links 
### ¿Que son los hard links?
Un hard link es una nueva referencia a un [[inode]]. 
Cuando creamos un hard link, el sistema añade una nueva entrada que apunta a un mismo [[inode]]. Por esta razón un archivo que contiene exactamente lo mismo que otro, puede tener varios nombres pero hace referencia al mismo espacio de almacenamiento en disco.
A simple vista los hard links parecieran una copia de un archivo, sin embargo esto es algo erroneo ya que el hard link no duplica el contenido del archivo sino que crea un nuevo nombre para el archivo.
![[hardlinks|1000]]

### Uso de hard links
La sintaxis para crear hard links es el siguiente comando.
```bash
ln archivo.txt archivo-hardlink.txt
```

### Ventajas de los hard links
Una ventaja muy potente que le veo a los hard link es la posibilidad de borrar un archivo y que este no se pierda por completo debido a que existen varias referencias al mismo inode. Aunque vale la pena aclarar que al eliminar la ultima referencia si se pierde el archivo por completo.
El archivo se pierde si el contador de enlaces llega a 0.
![[contador-hardlinks | 1000]]

### Como se pueden aplicar los hard links profesionalmente
Dado lo anteriormente explicado, una de las aplicaciones más importantes de los hard links en entornos profesionales es la **optimización del almacenamiento en copias de seguridad**.

En una estrategia de respaldo tradicional, cada nueva copia duplica todos los archivos mediante herramientas como `cp`. Esto puede convertirse en un proceso ineficiente tanto en consumo de espacio como en tiempo de ejecución, ya que, entre un respaldo y otro, la mayoría de los archivos suelen permanecer sin cambios.

Para solucionar este problema, algunas herramientas de respaldo emplean hard links para los archivos que no han sido modificados. En lugar de volver a copiar su contenido, se crea un nuevo nombre que apunta al mismo inode. Como resultado, el archivo solo ocupa espacio una vez en el disco, aunque aparezca en múltiples respaldos.

Si posteriormente un archivo cambia, entonces sí se crea una nueva copia con un inode diferente, mientras que los respaldos anteriores continúan haciendo referencia a la versión original. Gracias a esta estrategia es posible mantener múltiples copias de seguridad aparentando ser respaldos completos, pero utilizando una fracción del espacio que requeriría duplicar todos los archivos en cada ejecución.
### Notas Relacionadas
[[Soft-links]]
[[inode]]
[[Links]]
[[comandos-linux]]
