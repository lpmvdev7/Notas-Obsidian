Tipo: Nota permanente
Fecha: 2026-07-31
Referencias: 
* Linux.pdf
Temas: #Procesos 
### ¿Que hace el comando?
El comando nos muestra todos los procesos en ejecución dentro de nuestro sistema en tiempo real.

### Como se utiliza
La sintaxis de uso es muy sencilla
```bash
top
```

### ¿Que muestra top?
El comando muestra una tabla con varias columnas, los valores que muestra son los siguientes:
* PID: Identificador del proceso
* USER: usuario que ejecuta el proceso
* PR: prioridad del proceso
* NI: Nice value
* VIRT: Memoria virtual usada por el proceso
* RES: Memoria RAM usada por el proceso
* SHR: Memoria compartida
* S: Estado del proceso
	* R (Running)
	* S (Sleeping)
	* D (En espera)
	* T (Stoped)
	* Z (Zombie)
* %CPU: Porcentaje de CPU consumido en tiempo real.
* %MEM: Porcentaje de memoria consumido en tiempo real
* HORA+: Tiempo total consumido por el proceso
* ORDEN: Proceso que se ejecuta.

### Notas Relacionadas
[[ps]]
[[htop]]


