Tipo: Nota permanente
Fecha: 2026-09-04
Temas:  #Variable-especiales #Bash-script 
### ¿Que es?
La variable $! guarda el process id del utimo proceso ejecutado en segundo plano.

```bash
#!/bin/bash
read -p "Coloque el numero de veces que se ejecutara el ping: " numero

ping -c$numero 8.8.8.8&

# Uso de la variable especial $!
bpid=$!
echo "El PID del background process es $bpid"

wait "$bpid"
echo "El proceso ha terminado"
```

### Notas Relacionadas
[[Variable $0]]
[[Variable $GATO]]
[[Variable $@]]
[[Variable $ASTERISCO]]
[[Variable $$]]
[[Variable $-]]
[[Variable $PIPESTATUS]]
[[Variable $BASHPID]]


