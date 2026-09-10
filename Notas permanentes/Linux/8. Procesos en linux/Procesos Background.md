Tipo: Nota permanente
Fecha: 2026-07-31
Referencias:
* Linux.pdf 
Temas:  #Procesos 
### ¿Que son los procesos background?
Los procesos background son aquellos que no necesitan la interacción directa del usuario, son no bloqueantes. Por lo general cuando un proceso lleva demasiado tiempo se convierte en un proceso de background. 
Estos procesos al ser no bloqueantes nos permiten a nosotros como usuarios la interacción directa con la terminal, es decir que podemos seguir ejecutando comandos mientras estos siguen en ejecución.
Algunos procesos background que se me ocurren como ejemplo:
* Hacer el backup de una carpeta
* Tareas cron del servidor relacionadas a monitoreo de archivos y directorios

### ¿Como podemos iniciar un proceso Background?
Para iniciar un proceso background lo único que tenemos que hacer es colocar este signo **&** después del comando que estemos ejecutando.
```bash
comando&
```

```bash
sleep 100&
```

### Notas Relacionadas
[[bg]]
[[Procesos Foreground]]
[[jobs]]



