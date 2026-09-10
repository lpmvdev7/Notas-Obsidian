Tipo: Nota permanente
Fecha: 2026-07-24
Referencias:
* Linux.pdf
Temas:  #Linux #Compresion #Archivos 
### Comando zip
El comando zip nos ayuda a comprimir archivos y directorios de manera sencilla

### Uso del comando
Si lo que queremos es comprimir un archivo, hacemos lo siguiente: 
```bash
zip archivo.zip archivo.txt
```

En caso de que necesitemos comprimir un directorio colocamos la siguiente sintaxis.
```bash
zip -r directorio.zip directorio
```

### Caso de uso
>Trabajas en el área de soporte técnico de una agencia de publicidad. Un diseñador te escribe porque necesita enviarle a un cliente 5 archivos de una campaña (3 images .png, un .pdf y un .docx) que están todos en una carpeta llamada campana_cliente/. El correo de la empresa solo permite adjuntar un archivo a la vez, y el diseñador no sabe como hacer para mandarlos todos juntos.

### Solución
Volver zip la carpeta campana_cliente/
```bash
zip -r campana_cliente.zip campana_cliente
```

### Notas Relacionadas
[[tar]]
[[gzip]]
[[comandos-linux]]

