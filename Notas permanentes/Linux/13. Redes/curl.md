Tipo: Nota permanente
Fecha: 2026-08-13
Referencias:
* https://www.youtube.com/watch?v=n3NtrQYrjDw
* https://www.youtube.com/watch?v=3xmD4E2aqxo
Temas: 
### ¿Que hace el comando?
El comando curl es una herramienta muy poderosa de la linea de comandos que nos ayuda a muchas cosas, consultar información web, descargar archivos, testear APIs, en resumen es una herramienta muy versátil que como desarrolladores es indispensable aprender.

Abajo estaré dejando una pequeña documentación de las opciones que tiene el comando CURL.
```bash
-X # Opcion para especificar el metodo HTTP que queremos utilizar
-H # Anadir una cabecera HTTP
-d # Enviar datos a una peticion
-O # Guardar el archivo usando el nombre que tiene en la URL
-o # Guardar la respuesa un nombre que eligamos
-f # Falla silenciosa ante errores (404, 500, etc)
-s # Ocultamos el progreso y los mensajes normales
-S # Mostramos errores incluso si -s esta activo
-L # Seguimos las redirecciones HTTP
-I # Hacemos una peticion HEAD obteniendo solamente las cabeceras
-i # Incluimos las cabeceras HTTP en la salida
-v # Modo verbose que nos ayuda a entender lo que esta pasando
-F # Enviar datos como multipart/form-data
-u # Autenticacion con usuario y contraseña
-b # Trabajar con cookies
-c # Trabajar con cookies
--retry # Reintentar si falla
--max-time # Establecer un tiempo de maximo de toda la operacion
```
### Uso
```bash
# Hacer un GET con curl
curl https://jsonplaceholder.typicode.com/posts/1

# Hacer un GET con curl de forma explicita
curl -X GET https://jsonplaceholder.typicode.com/posts/1

# Hace un POST con curl
curl -X POST https://jsonplaceholder.typicode.com/posts \
	 -H "Content-Type: application/json" \
	 -d '{"title": "Mi Post", "body": "Hola mundo", "userId": 1}'

# Cargar un token de acceso usando CURL, para consumir una API.
curl https://api.ejemplo.com/datos \
	-H "Authorization: Bearer TU_API_KEY"

# Descargar un archivo con curl
curl -O https://example.com/archivo.zip

# Descargar un archivo con curl asignandole un nombre
curl -o ~/Descargas/archivo.zip https://example.com/archivo.zip

# Descargar software con curl e imprimir en stdout el contenido, esto sirve mucho cuando instalamos scripts de terceros.
curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh 

# Acceder a los hedader de una peticion
curl -I https://donweb.com

# Rellenar un formulario simple
curl -X POST https://ejemplo.com/formulario \
	-d "nombre=Juan"
	-d "email=juan@correo.com"
	-d "mensaje=Hola"
```

>En mi caso como desarrollador de software estaré usando curl para probar APIs, para ello vale la pena recomendar el comando **jq** que embellece el json resultante de consultas curl.

### Ejemplo del comando
Con el objetivo de practicar curl,  he creado una api para una pizzeria la cual me permita hacer pruebas con curl.

>Obtener solamente las pizzas disponibles
```bash
curl -sX GET localhost:8000/pizzas?disponible=true | jq
```

>Obtener las pizzas clásicas
```bash
curl -sX GET localhost:8000/pizzas?categoria=Clasica | jq
```

>Crear una pizza
```bash
curl -X POST "http://localhost:8000/pizzas" \
  -H "X-API-Key: pizza-secret" \
  -H "Content-Type: application/json" \
  -d '{"nombre":"Little Caesars","descripcion":"Pizza a 99 varos", "precio":100, "categoria":"Hot-N-Ready", "disponible":true}'
```

>Modificar completamente una pizza con PUT
```bash
curl -sX PUT "http://localhost:8000/pizzas/1" \
  -H "X-API-Key: pizza-secret" \
  -H "Content-Type: application/json" \
  -d '{"nombre": "Dominos pizza", "descripcion": "La pizza que domina", "precio": 149, "categoria": "Clasica", "disponible": true}' | jq
```

>Modificar solamente el precio con PATCH
```bash
curl -X PATCH "http://localhost:8000/pizzas/1" \
  -H "X-API-Key: pizza-secret" \
  -H "Content-Type: application/json" \
  -d '{"nombre": "Dominos pizza", "descripcion": "La pizza que domina", "precio": 1500, "categoria": "Clasica", "disponible": true}' | jq
```

> Eliminar una pizza
```bash
curl -X DELETE localhost:8000/pizzas/1
```

>Crear un pedido
```bash
curl -X POST localhost:8000/pedidos \
	-H "content-type: application/json" \
	-d '{"cliente": "Pablo", "direccion": "Calle San Jose #119", "pizza_id": 2, "cantidad": 3, "estado": "recibido"}'
```

>Subir una imagen
```bash
curl -X POST http://127.0.0.1:8000/upload \
  -F "archivo=@/home/pablo/Descargas/pizza.jpg"
```

>Descargar el menú
```bash
curl -O localhost:8000/menu.txt
```

### Notas Relacionadas
[[comandos-linux]]
[[wget]]

