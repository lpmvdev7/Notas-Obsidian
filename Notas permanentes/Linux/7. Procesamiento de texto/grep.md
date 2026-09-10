Tipo: Nota permanente
Fecha: 2026-07-29
Referencias:
* Linux.pdf
Temas:  #Archivos #Procesamiento-texto
### ¿Que hace el comando grep?
El comando grep encuentra las coincidencias que le indiquemos dentro de un texto. Es un comando que nos ayuda encontrar patrones en archivos de texto.

### Como utilizar el comando
Al igual que la gran mayoría de comandos de linux, grep es un comando que nutre su funcionalidad mediante el uso de sus opciones, a continuación mostrare la sintaxis de uso para estas opciones junto con un enunciado que ayude a comprender en que casos esto ayude y en que otros no.

Cuando queremos encontrar un patrón en texto, utilizamos la siguiente sintaxis.
```bash
grep "gat" gato.txt
```

En ocasiones querremos encontrar frases enteras dentro de texto, o incluso escanear archivos de correo en busca de un dato especifico.  Para ello tenemos la opción **-F**
```bash
grep -F "cadena_exacta" archivo.txt
```

Cuando queramos buscar una palabra en especifico pero no sepamos en donde buscar, podemos utilizar la opción **-r**, esta opción se encarga de buscar recursivamente un patrón dentro de un directorio.
```bash
grep -r "texto" Escritorio/
```

El comando grep también nos permite el uso de búsqueda de patrones mediante expresiones regulares, esto con las opciones **-E** y **-P**
```bash
# inventario.txt
Producto: Laptop-X200, Precio: $899.99, Stock: 15
Producto: Mouse-M10, Precio: $19.50, Stock: 230
Producto: Teclado-K88, Precio: $45.00, Stock: 0
Producto: Monitor-27M, Precio: $199.99, Stock: 8
Pedido #A1023 realizado el 2024-01-15 por cliente@tienda.com
Pedido #A1024 realizado el 2024-02-03 por maria.lopez@correo.com
Pedido #B2050 realizado el 2023-12-25 por juan_perez99@mail.org
Estado: ENVIADO
Estado: pendiente
Estado: Cancelado
Estado: entregado
IP de acceso: 192.168.1.10
IP de acceso: 10.0.0.255
IP de acceso: 256.1.1.1
Código postal: 28001
Código postal: CP-45678
Descuento aplicado: 10%
Descuento aplicado: 25%
Sin descuento aplicado
Contacto soporte: +34 612 345 678
Contacto soporte: +1-800-555-0199
Nota: entrega antes de las 18:00 hrs
Nota: entrega antes de las 09:30 hrs
URL: https://tienda.com/producto/laptop-x200
URL: http://tienda.com/producto/mouse-m10
Fin del inventario.

```

```bash
# Encontramos las fechas que se encuentran en el archivo
grep -E '[0-9]{4}-[0-9]{2}-[0-9]{2}' inventario.txt 
```

```bash
# Encontrar los correos que se encuentran en el archivo
grep -Po "\w+@\w+\.\w+" inventario.txt 
```

El comando grep también se puede utilizar junto con los pipelines.
```bash
cat inventario.txt | grep -Po "\w+@\w+\.\w+"
```

### Notas Relacionadas
[[comandos-linux]]
[[Regex]]
[[Pipelines]]
