Tipo: Nota permanente
Fecha: 2026-08-07
Referencias:
* Linux.pdf
Temas: #Almacenamiento #filesystem 
### ¿Que hace el comando?
El comando fdisk es una utilidad de la linea de comandos en linux que nos permite manipular la tabla de particiones del sistema operativo.

### Sintaxis del comando
Listar las particiones del sistema
```bash
sudo fdisk -l
```

El comando anterior nos ayuda a identificar un disco, ese disco lo podemos pasar como argumento al modo interactivo del comando, de la siguiente manera:
```bash
sudo fdisk /dev/dispostivo
```

### Usando el modo interactivo
Para este pequeño ejemplo he colocado una memoria USB cuyo nombre en el almacenamiento es /dev/sda
```bash
sudo fdisk /dev/sda

Bienvenido a fdisk (util-linux 2.39.3).
Los cambios solo permanecerán en la memoria, hasta que decida escribirlos.
Tenga cuidado antes de utilizar la orden de escritura.

Este disco está actualmente en uso - no se aconseja volver a crear particiones.
Se recomienda desmontar todos los sistemas de ficheros y deshacer todas las
particiones de intercambio de este disco.


Orden (m para obtener ayuda): 
```

Entramos a un menu interactivo en el cual podremos realizar todas las operaciones relacionadas a particiones en nuestro dispositivo de almacenamiento. Si escribimos m se nos mostraran todas las opciones.
```bash
sudo fdisk /dev/sda

Bienvenido a fdisk (util-linux 2.39.3).
Los cambios solo permanecerán en la memoria, hasta que decida escribirlos.
Tenga cuidado antes de utilizar la orden de escritura.

Este disco está actualmente en uso - no se aconseja volver a crear particiones.
Se recomienda desmontar todos los sistemas de ficheros y deshacer todas las
particiones de intercambio de este disco.


Orden (m para obtener ayuda): m

Ayuda:

  DOS (MBR)
   a   conmuta el indicador de iniciable
   b   modifica la etiqueta de disco BSD anidada
   c   conmuta el indicador de compatibilidad con DOS

  General
   d   borra una partición
   F   lista el espacio libre no particionado
   l   lista los tipos de particiones conocidos
   n   añade una nueva partición
   p   muestra la tabla de particiones
   t   cambia el tipo de una partición
   v   verifica la tabla de particiones
   i   imprime información sobre una partición

  Miscelánea
   m   muestra este menú
   u   cambia las unidades de visualización/entrada
   x   funciones adicionales (sólo para usuarios avanzados)

  Script
   I   carga la estructura del disco de un fichero de script sfdisk
   O   vuelca la estructura del disco a un fichero de script sfdisk

  Guardar y Salir
   w   escribe la tabla en el disco y sale
   q   sale sin guardar los cambios

  Crea una nueva etiqueta
   g   crea una nueva tabla de particiones GPT vacía
   G   crea una nueva tabla de particiones SGI (IRIX) vacía
   o   crea una nueva tabla de particiones vacía en el MBR (DOS)
   s   crea una nueva tabla de particiones Sun vacía

```

### Notas Relacionadas
[[comandos-linux]]
[[Archivo fstab]]
[[mkfs]]

