Tipo: Nota permanente
Fecha: 2026-09-04
Temas: #Bash-script #Variable-especiales 
### ¿Que es?
La variable especial $PIPESTATUS es un array especial en bash que contiene todos los exit code de aquellos comandos que forman parte de un pipeline.

```bash
echo "Hola mundo" | cowsay | lolcat
echo "Argumentos: $*"
echo "${PIPESTATUS[@]}"
```

```bash
< Hola mundo >
 ------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
0 0 0 # <- Esto serian los status code 
```

$PIPESTATUS nos ayuda a depurar errores en un pipeline, dado que es un array podemos iterarlo y modificar nuestro script de cierta manera dado un status code, esto hace que nuestros scripts sean mas robustos y menos propensos a errores.
### Notas Relacionadas
[[Variable $0]]
[[Variable $GATO]]
[[Variable $@]]
[[Variable $ASTERISCO]]
[[Variable $$]]
[[Variable $!]]
[[Variable $-]]
[[Variable $BASHPID]]


