Tipo: Nota permanente
Fecha: 2026-08-27
Referencias:
* Linux.pdf
Temas: #Bash-script #filesystem 
### ¿Donde se ubican los ejecutables en nuestro sistema?
En sistemas tipo unix como linux cuando entramos a la terminal por lo general lo hacemos con el propósito de ejecutar comandos, estos comandos viven en la siguiente ubicación del sistema de archivos.
```
/usr/bin
```
Dentro se encuentran varios de los comandos que usamos dentro de la terminal, esto lo hace una ubicación ideal para nuestros scripts.

También vale la pena mencionar el directorio sbin.
```bash
/sbin
```
Dentro se encuentran comandos de administración.

Por ultimo y no menos importante, nuestros scripts pueden ser alojados en cualquier carpeta que queramos siempre, los scripts funcionaran correctamente siempre y cuando la carpeta se encuentre referenciada en PATH.
```bash
echo $PATH
```

### Ubicando nuestros scripts.
Ahora que conocemos varias opciones para ubicar nuestros scripts, vale la pena mencionar que la ubicación de estos debe verse influenciada por la funcionalidad que estos aportan al sistema.

#### Ejemplo 1 - Ubicando nuestros scripts en /usr
Nos dirigimos a la carpeta /usr y dentro creamos una carpeta llamada scripts.
```bash
cd /usr
sudo mkdir scripts
```

Dentro de la carpeta scripts creamos un nuevo archivo con extension .sh
```bash
#saludito.sh

#! /bin/bash
echo "Hola a todos desde este nuevo script"
```

Le damos permisos de ejecución a nuestro archivo.
```bash
sudo chmod +x saludito.sh
```

Agregamos al PATH la siguiente ruta:
```bash
/usr/scripts

export PATH="$PATH:/usr/scripts"
```

Ahora desde cualquier ubicación podemos ejecutar.
```
saludito.sh
```

Incluso podemos darle un alias a nuestro script.
```bash
alias saludito="saludito.sh"

# Ahora lo podemos llamar de la siguiente manera
saludito
```
### Ejemplo 2 - Ubicando nuestros scripts en cualquier lugar.
Creamos un nuevo directorio
```bash
mkdir personal_scripts
```

Imprimimos la ruta y la colocamos en el PATH.
```bash
cd personal_scripts

pwd

export PATH="$PATH:/home/pablo/personal_scripts"
```

Dentro de personal_scripts creamos un nuevo archivo sh.
```bash
#! /bin/bash

echo "Bienvenido a tu $HOME, $USER"
```

Asignamos permisos de ejecución
```bash
chmod +x greet.sh
```

Ahora desde cualquier lugar podremos ejecutar nuestro script.
```bash
greet.sh
```

>La variable PATH vuelve a su estado original cada vez que iniciamos una nueva terminal, si queremos que el valor de esta persista, tenderemos que modificar el archivo .bashrc colocando la variable PATH con las modificaciones que hicimos.
### Notas Relacionadas
[[Sistema de archivos]]
[[Permisos en Linux]]
[[PATH]]
[[alias]]
[[sudo]]
[[shebang]]



