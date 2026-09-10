Tipo: Nota literatura | Nota permanente
Fecha: 2026-07-30
Referencias:
* 
Temas: #Comandos 
### ¿Que son los alias en linux?
Los alias son aquellos apodos que colocamos a una secuencia de comandos que no queremos repetir una y otra vez.
Los alias por lo general son utilizados cuando tenemos un proceso muy repetitivo o cuando un comandos es demasiado largo para recordar todas sus opciones, en estos casos los alias representan una solución ideal ya que nos ayudan a ponerle un sobrenombre reconocible a esas secuencias.
También se podría decir que los alias es una de las tantas formas que ofrece linux para poder crear nuestros propios comandos.

Vemos este comando
```bash
find /var -type f -name "*.log" 2>/dev/null
```

El comando anterior se encarga de buscar todos los archivos log a los que tiene permiso el usuario actual, en base a eso podemos crearle un alias al comando para reflejar lo que este hace.
```bash
alias findlog='find /var -type f -name "*.log" 2>/dev/null'
```

Pero ahora tenemos un problema, nuestro alias no sobrevivirá a esta sesión de la shell. Para que podamos seguir usando nuestro alias tenemos que copiar y pegar su definición en el archivo .bashrc, de esta manera podremos seguir usando nuestro alias.

### Notas Relacionadas
[[Sesiones linux]]
[[PATH]]


