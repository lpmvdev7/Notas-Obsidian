Tipo: Nota permanente
Fecha: 2026-08-04
Referencias:
* Linux.pdf
Temas: #daemons 
### ¿Que hace el comando?
El comando pstree nos muestra en un formato de árbol una jerarquía de todos los procesos del sistema, empezando desde el proceso con PID 1 el cual seria systemd.

```bash
pstree
systemd─┬─ModemManager───3*[{ModemManager}]
        ├─NetworkManager───3*[{NetworkManager}]
        ├─accounts-daemon───3*[{accounts-daemon}]
        ├─agetty
```


### Notas Relacionadas
[[comandos-linux]]
[[systemctl]]
[[systemd]]


