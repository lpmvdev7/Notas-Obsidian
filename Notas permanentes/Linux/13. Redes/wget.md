Tipo: Nota permanente
Fecha: 2026-08-13
Referencias:
* Linux.pdf
Temas:
* #Redes #Archivos 
### ¿Que hace el comando?
El comando wget es una utilidad de la linea de comandos en linux que nos ayuda a descargar desde internte. Con Wget podemos descargar archivos usando HTTP, HTTPS y FTP.
El comando provee de una variedad amplia de opciones que nos permite descargar múltiples archivos, ver detalles de las descargas, limitar el uso de banda ancha, descargas recursivas, descargar en segundo plano, replicar un sitio web y mucho mas.

### Uso del comando
```bash
# Descargar una imagen de internet con wget
wget https://img.a.transfermarkt.technology/portrait/big/418560-1709108116.png?lm=1

# Con la opcion -O podemos colocarle nombre al archivo descargado.
wget -O haaland.jpg https://img.a.transfermarkt.technology/portrait/big/418560-1709108116.png?lm=1

# Descargar el archivo en un directorio especifico (este jala mas chido)
wget -O Descargas/yeilend.png https://img.a.transfermarkt.technology/portrait/big/418560-1709108116.png?lm=1

# Descargar el archivo en un directorio especifico
wget -P Descargas/ https://img.a.transfermarkt.technology/portrait/big/418560-1709108116.png?lm=1

# Descargar recursivamente el contenido de un archivo de texto
cat imgPinterest.txt 
https://i.pinimg.com/736x/c0/41/aa/c041aa25ed40c6b9a2d7b60e4824ea20.jpg
https://i.pinimg.com/1200x/d7/e5/8a/d7e58aad178bcf9e3ea5f042d560f525.jpg
https://i.pinimg.com/736x/fd/d8/c4/fdd8c49375b3643c8254dda7f3dcf987.jpg
https://i.pinimg.com/736x/4f/f9/d9/4ff9d9352d1b274c42d85776c6c75e9e.jpg

wget -i imgPinterest.txt
```
### Notas Relacionadas
[[comandos-linux]]
[[curl]]
[[gsettings]]
[[dconf]]
