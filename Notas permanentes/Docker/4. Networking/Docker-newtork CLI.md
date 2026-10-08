Tipo: Nota permanente
Fecha: 2026-10-07
Referencias:
* 
Temas: #CLi #Docker #networking-docker 
### Comandos para trabajar con redes en docker
A continuación presentaremos aquellos comandos que nos proporciona docker para trabajar con networking en contenedores.
```bash
# Crear una red 
docker network create <red>

# Conectar un contenedor a una red
docker network connect <red> <contenedor>

# Desconectar un contenedor de la red
docker network disconnect <red> <contenedor>

# Listar las redes docker existentes
docker network ls

# Eliminar una o mas redes
docker network rm <red>

# Eliminar aquellas redes que no se estan usando
docker network prune
```

### Notas Relacionadas
[[Redes en docker]]
[[Tipos de Redes en Docker]]
[[Topologia de red con docker networking]]
