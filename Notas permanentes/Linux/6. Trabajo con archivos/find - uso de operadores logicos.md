Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-27
Referencias:
*  https://youtu.be/SLXYEnqmEgU?si=TJvFNNgsIT6dfNqm
Temas: #Archivos #Linux 
### ¿Para que sirven los operadores lógicos en el comando find?
El comando find nos permite realizar consultas mediante el uso de los operadores lógicos: NOT, AND y OR, el uso de estos operadores enriquece nuestras consultas con find ya que de esta manera podemos crear lógica tan compleja como queramos con el objetivo de encontrar archivos o directorios.

### Casos de uso para cada operador lógico.
#### AND
El servidor almacena miles de vídeos y el equipo de infraestructura necesita localizar únicamente los archivos de vídeo que:
* sean archivos normales
* tengan extensión .mp4
* ocupen mas de 2GB
La búsqueda debe realizarse en: **/media**

```bash
find /media \( -type f -a -name "*.mp4" -a -size +2G \)
```

#### OR
Durante una migración se deben localizar todos los archivos de diseño. Los diseñadores trabajan únicamente con:
* Photoshop (.psd)
* Ilustrator (.ai)
La búsqueda debe realizarse en: **/proyectos/disenos**
```bash
find /proyectos/disenos -type f \( -name "*.psd" -o -name "*.ai" \)
```

#### NOT
Antes de realizar un respaldo se deben localizar todos los archivos del proyecto, excepto aquellos con extensión **.tmp**, ya que son archivos temporales.
La búsqueda debe comenzar en: **/var/www**
```bash
find /var/www -type f -not -name "*.tmp"
```

#### Caso de uso unificado
El área de TI realizara una auditoria de seguridad.
Necesita localizar archivos que cumplan estas condiciones:
* Sean archivos normales
* Tengan extensión .conf o .cfg
* Midan mas de 10KB
* No pertenezcan al usuario root
* No estén dentro de ningún directorio llamado backup.
La búsqueda comienza en: **/etc**
```bash
find /etc -path "*/backup" -prune -o -type f -size +10K -not -user root \( -name "*.conf" -o -name "*.cfg" \)
``` 

### Notas Relacionadas
[[find]]
[[find - expresiones de busqueda]]
[[find - expresiones de filtrado]]
[[find - acciones sobre archivos]]
[[Uso de operadores logicos en la terminal]]
[[Algebra de Bool]]