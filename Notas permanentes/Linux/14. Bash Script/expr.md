Tipo: Nota permanente
Fecha: 2026-08-28
Referencias:
* Linux.pdf
Temas: #Bash-script 
### ¿Que hace el comando?
expr es un comando que nos ayuda a evaluar expresiones, principalmente expresiones matemáticas o cadenas.
```bash
expr 10 - 3
expr 10 \* 3
expr 10 / 2
expr 10 % 3
```

### Otros usos del comando
```bash
# Obtener la cantidad de caracteres de un cadena
expr length "hola"

# Extraer una parte de la cadena
expr substr "Linux" 1 3 

# Buscar un patron al principio de la cadena y devolver cuantos caracteres coiniciden
expr match "hola123" "hola"

# Buscar la posicion del primer caracter que aparezca de un conjunto de caracteres
expr index "hola" "a"

```

### Notas Relacionadas
[[Bash Scripting]]


