Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-30
Referencias:
* Linux.pdf
Temas: #Procesamiento-texto #Archivos #Linux 
### Sobre uniq
uniq es el comando encargado de eliminar duplicados en un archivo de texto. 
>Vale la pena mencionar que uniq va de la mano con sort, esto es debido a que  uniq solo detecta duplicados en lineas de texto consecutivas, por esta razón si recibimos un archivo con duplicados pero que no tiene sort alguno, uniq no funcionara.

Tenemos el siguiente archivo con correos electrónicos.
```text
ana@gmail.com
carlos@gmail.com
ana@gmail.com
mariana@outlook.com
jlhernandez@yahoo.com
mariana@outlook.com
```

Haciendo uso de pipelines podemos ver que el comando uniq elimina los duplicados en un archivo de texto.
```bash
cat correos.txt | sort | uniq
ana@gmail.com
carlos@gmail.com
jlhernandez@yahoo.com
mariana@outlook.com
```
 
### Notas Relacionadas
[[comandos-linux]]
[[sort]]
[[Pipelines]]

