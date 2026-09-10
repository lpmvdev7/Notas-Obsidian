Tipo: Nota permanente
Fecha: 2026-07-17
Referencias:
* Linux.pdf
Temas: #Flujos-estandar #Linux
### ¿Que son los flujos estándar en linux?
Los flujos estándar son la manera que tienen los proceso en linux de comunicarnos a nosotros como usuarios el estado de un proceso.
Se dividen en tres categorías:
* stdin: aqui es cuando el proceso lee las entradas del teclado
* stdout: la respuesta del proceso mostrada como texto en la terminal
* stderr: El proceso muestra un mensaje de error.

**stdin**
```bash
ls
```

**stdout**
```bash
ls
backup-repos.list          blender-5.0.1-linux-x64  Descargas   Escritorio  Imágenes    markitdown  Ninebox-new       package.json  Plantillas  pt       restaurante   salida.html  themes
Base-de-datos-restaurante  cacafire                 Documentos  examplemv   key-gh.pem  Música      nuevo_nombre.txt  PDF           Proyectos   Público  resultadoCSS  snap         Vídeos

```

**stderr**
```bash
cat archivo.txt
cat: archivo.txt: No existe el archivo o el directorio
```
### Notas Relacionadas
[[comandos-linux]]
[[Redireccionamiento]]

