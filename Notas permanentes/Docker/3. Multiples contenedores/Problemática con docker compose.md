Tipo: Nota permanente
Fecha: 2026-10-03
Referencias:
* 
Temas: #Dockerfile #docker-compose  
### Pequeño proyecto usando compose
A continuación presento la estructura de carpetas de un proyecto conformado por la creación de frontend y backend.
```bash
compose-docker/
├── backend/
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
│
├── frontend/
│   ├── Dockerfile
│   └── index.html
│
└── compose.yml
```

#### Frontend
Para la creación del frontend coloque todo el html, css y javascript dentro de un archivo.
```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Perfil de usuario</title>
<style>
  :root {
    --bg: #eef2f6;
    --card: #ffffff;
    --text: #14202e;
    --muted: #5d6b7a;
    --accent: #1f5fbf;
    --line: #d5dde6;
  }
  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #0f1722;
      --card: #172230;
      --text: #e8eef5;
      --muted: #94a3b3;
      --accent: #6aa4f5;
      --line: #263548;
    }
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    min-height: 100vh;
    display: grid;
    place-items: center;
    padding: 1.5rem;
    background: var(--bg);
    color: var(--text);
    font-family: Georgia, "Times New Roman", serif;
  }
  main { width: 100%; max-width: 420px; }
  .card {
    background: var(--card);
    border: 1px solid var(--line);
    border-radius: 14px;
    overflow: hidden;
  }
  .card img {
    display: block;
    width: 100%;
    aspect-ratio: 3 / 2;
    object-fit: cover;
    background: var(--line);
  }
  .info { padding: 1.4rem 1.5rem 1.6rem; }
  h1 { margin: 0 0 .2rem; font-size: 2rem; font-weight: 700; }
  .puesto { margin: 0 0 1.2rem; color: var(--muted); font-size: 1.05rem; }
  .edad {
    display: inline-block;
    padding: .25rem .7rem;
    border: 1px solid var(--accent);
    border-radius: 999px;
    color: var(--accent);
    font-family: system-ui, sans-serif;
    font-size: .9rem;
  }
  .estado {
    padding: 2rem 1.5rem;
    text-align: center;
    color: var(--muted);
    font-family: system-ui, sans-serif;
  }
  .estado code { color: var(--text); }
  button {
    margin-top: 1rem;
    padding: .55rem 1.1rem;
    border: 0;
    border-radius: 8px;
    background: var(--accent);
    color: #fff;
    font: inherit;
    font-family: system-ui, sans-serif;
    cursor: pointer;
  }
  button:focus-visible { outline: 3px solid var(--accent); outline-offset: 2px; }
</style>
</head>
<body>
<main>
  <div class="card" id="tarjeta">
    <div class="estado">Cargando usuario…</div>
  </div>
</main>

<script>
  // Cambia esta URL si tu API corre en otro puerto o servidor
  const API_URL = "http://127.0.0.1:3000";

  const tarjeta = document.getElementById("tarjeta");

  function escapar(texto) {
    const div = document.createElement("div");
    div.textContent = texto;
    return div.innerHTML;
  }

  async function cargarUsuario() {
    tarjeta.innerHTML = '<div class="estado">Cargando usuario…</div>';
    try {
      const respuesta = await fetch(`${API_URL}/usuario`);
      if (!respuesta.ok) throw new Error(`Error ${respuesta.status}`);
      const u = await respuesta.json();

      // En tu API la clave se llama "Imagen:" (con dos puntos); acepto ambas
      const imagen = u["Imagen:"] || u["Imagen"] || "";

      tarjeta.innerHTML = `
        ${imagen ? `<img src="${escapar(imagen)}" alt="Foto de ${escapar(u.Nombre)}">` : ""}
        <div class="info">
          <h1>${escapar(u.Nombre)}</h1>
          <p class="puesto">${escapar(u.Puesto)}</p>
          <span class="edad">${escapar(String(u.Edad))} años</span>
        </div>`;
    } catch (error) {
      tarjeta.innerHTML = `
        <div class="estado">
          No se pudo conectar con la API en <code>${escapar(API_URL)}</code>.
          <br>Verifica que el servidor esté corriendo y que CORS esté habilitado.
          <br><button id="reintentar">Reintentar</button>
        </div>`;
      document.getElementById("reintentar").addEventListener("click", cargarUsuario);
    }
  }

  cargarUsuario();
</script>
</body>
</html>

```

#### Backend
Para el backend utilice fastAPI.
```bash
from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware

app = FastAPI()

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_methods=["*"],
    allow_headers=["*"]
)

@app.get("/")
async def root():
    return {"message":"Hello world"}

@app.get("/usuario")
async def usuario():
    usuario = {
        "Nombre": "Pablo",
        "Puesto": "Desarrollador de software",
        "Edad": 24,
        "Imagen:" :'https://d2qbblo43j0vwz.cloudfront.net/wp-content/uploads/2024/10/645301-min-1024x683.webp'
    }
    return usuario
```


#### Dockerfiles
Tanto backend como frontend tiene un dockerfile asociado en sus respectivas carpetas.
```dockerfile
# Backend
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["uvicorn","--host","0.0.0.0","--port","3000","app:app"]
```

```dockerfile
# Frontend
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

#### Docker compose
En la raíz del proyecto creamos un archivo compose.yml 
```bash
services:
  frontend:
    build:
      context: './frontend'
      dockerfile: dockerfile
    ports:
      - '8081:80' 

  backend:
    build:
      context: './backend'
      dockerfile: dockerfile
    ports:
      - '3000:3000'
```

Ejecutamos el siguiente comando:
```bash
docker compose up -d
```

Así se vería nuestro frontend.
![[frontend-docker.png]]

y así se vería la documentación de nuestro backend
![[backend-docker.png]]

#### Conclusiones
Este pequeño proyecto me permitió practicar varios de los temas que he estado viendo con docker, los primero que hice fue mantener un enfoque individual por cada aplicación, es decir, primero hice el backend, arme el requirements.txt y una vez tenia funcionando esto correctamente procedí a implementar el dockerfile, y volví a aplicar esta metodología para el frontend. Esto me permitió practicar la sintaxis de los dockerfile y la creación de imágenes con etiquetas con el comando docker build -t. Una vez verifique que los dockerfile de ambos proyectos funcionaban correctamente me dispuse a moverme a la raiz del proyecto y alli crear un compose.yml para indicarle a docker que mediante el comando docker compose up -d me levantara los contenedores de backend y frontend. 
Me encanto realizar este pequeño proyecto ya que pude poner en practica lo que he estado aprendiendo estas ultimas semanas, esto no hace mas que emocionarme, ya que en un futuro podre implementar estos conocimientos en proyectos mas complejos.

### Notas Relacionadas
[[docker run vs docker compose]]
[[Estructura de un yaml para docker compose]]
[[docker-compose cli]]
[[docker netwroking]]
[[Compose files con redes]] 
[[Problemática con docker compose]]


