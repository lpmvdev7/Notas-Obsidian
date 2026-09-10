Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
El comando se encarga de reasignar la prioridad que tiene un proceso.

### Sintaxis del comando
```bsah
renice [nuevo_valor] -p PID
```

### Caso de uso del comando
Tenemos un ecomerce que vende productos para mascotas. El administrador inicia un respaldo del sitio web sin usar nice.
```bash
tar -czf petcommerce_bak.tgz /var/www/petcommerce
```

Despues de unos minutos, nos damos cuenta que este proceso conlleva una gran cantidad de CPU, lo que ralentiza el tiempo de respuesta del sitio web.
Debido a que las prioridades del negocio se encuentran en atender primero a los clientes tenemos que asignar como prioridad el sitio web, para hacerlo tendremos que reasignar la prioridad del proceso encargado del backup.
Lo primero que haces es buscar el PID del proceso
```bash
ps aux | grep tar
```

Una vez que tenemos el PID disminuimos la prioridad del proceso.
```bash
renice 19 -p 2841
```

### Notas Relacionadas
[[comandos-linux]]
[[nice]]

