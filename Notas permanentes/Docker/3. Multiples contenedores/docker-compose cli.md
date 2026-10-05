Tipo: Nota permanente
Fecha: 2026-10-04
Referencias:
* 
Temas: #docker-compose #docker-compose-cli #CLi #Docker #Contenedores 
### Sobre la CLI de docker compose
La CLI de docker compose nos permite ejecutar operaciones sobre nuestras aplicaciones multicontenedor, a continuación estaré mostrando algunos de los comandos mas útiles de esta CLI.
```bash
# Levantar nuestros contenedores en segundo plano a partir de un archivo .yml
docker compose up -d

# Parar y eliminar contenedores
docker compose down

# Ver los contenedores en ejecuccion
docker compose ps

# Ver todos los logs de nuestros contenedores 
docker compose logs

# Ver los logs en especifico de un servicio
docker compose logs [servicio]

# Ejecutar comandos en un contenedor
docker compose exec [servicio] [comando]

# Pausar los procesos de los contendores
docker compose pause

# Continuar los procesos de los contenedores pausados
docker compose unpause

# Crear un contenedor nuevo para ejecutar un comando
docker compose run [servicio]

# Mostrar estadisticas de uso de los contenedores
docker compose stats
```

### Notas Relacionadas
[[docker run vs docker compose]]
[[Estructura de un yaml para docker compose]]
[[Problemática con docker compose]]



