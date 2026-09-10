Tipo: Nota permanente
Fecha: 2026-07-30
Referencias:
* Linux.pdf
Temas:  #Archivos #Procesamiento-texto #Comandos 
### Sobre el comando
El comando wc, cuenta las lineas palabras y caracteres.
* **-l**: lines
* **-w:** words
* **-c:** characters

Tenemos el siguiente archivo.
```bash
# correos.txt
ana@gmail.com
carlos@gmail.com
ana@gmail.com
mariana@outlook.com
jlhernandez@yahoo.com
mariana@outlook.com
```

#### Contamos la lineas del archivo
```bash
cat correos.txt | wc -l
6
```

#### Contamos las palabras en el archivo
```bash
cat correos.txt | wc -w
6
```

#### Contamos los caracteres en un archivo+
```bash
cat correos.txt | wc -c
107
```

### Notas Relacionadas
[[comandos-linux]]


