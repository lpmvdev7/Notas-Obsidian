Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
El comando disown va muy de la mano con el comando jobs, este comando se encarga de eliminar un proceso de la lista de trabajos.
Su caso de uso mas importante es la persistencia de los procesos una vez cerramos sesión en la terminal, en otras palabras permite que un proceso siga su curso incluso si nosotros cerramos la computadora y nos vamos a hacer otras cosas.

### Uso del comando
Ponemos a dormir a la terminal por 200 segundos, mandando el proceso a segundo plano
```bash
sleep 200 &
```

Listamos los jobs
```bash
jobs
```

Pasamos como argumento el numero de job a el comando disown
```bash
disown %1
```

Cerramos la terminal, volvemos a entrar y si ejecutamos el comando jobs de nuevo, nos daremos cuenta que nuestro proceso ya no se encuentra listado

SI queremos ver nuestro proceso tenemos que usar el comando ps para listarlo
```bash
 ps -aux | grep "sleep"
```
### Notas Relacionadas
[[jobs]]
[[Procesos Background]]
[[ps]]


