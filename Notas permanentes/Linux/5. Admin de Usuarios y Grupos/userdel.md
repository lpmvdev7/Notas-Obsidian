Tipo: Nota permanente
Fecha: 2026-07-22
Referencias:
* Linux.pdf
Temas:  #Comandos #Linux #usuarios 
### ¿Que hace el comando?
El comando userdel se encarga de eliminar a un usuario en sistemas linux.

### Uso del comando
```bash
 - Elimina un usuario:
   sudo userdel usuario

 - Elimina un usuario en otro directorio raíz:
   sudo userdel [-R|--root] ruta/al/otro/root usuario

 - Elimina un usuario junto con su directorio home y correo (mail spool):
   sudo userdel [-r|--remove] usuario
```

### Caso de uso para userdel
Laura es una desarrolladora full-stack en la empresa it-solutions, lamentablemente su desempeño no ha sido el esperado, es por ello que laura sera dimitida de su cargo, como parte del proceso, se necesita que el departamento de TI elimine el usuario de laura del servidor lo antes posible, como eliminarías el usuario de laura?

#### Solución a la problemática
Como principal responsable del area de TI en la empresa propondría dos soluciones.

La primer solución consiste en eliminar a laura como usuario definitivamente, esto quiere decir borrar su home y todo el trabajo que hizo ella.
```bash
userdel laura -r
```

La segunda solución consiste en únicamente eliminar a laura como usuario pero preservar su directorio home y así preservar su trabajo para la posteridad.
```bash
userdel laura
```

### Notas Relacionadas
[[Usuarios]]
[[useradd]]
[[usermod]]
[[who]]
[[passwd]]
[[comandos-linux]]
