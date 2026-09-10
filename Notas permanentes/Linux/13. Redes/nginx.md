Tipo: Nota permanente
Fecha: 2026-08-14
Referencias:
* Linux.pdf
* https://www.youtube.com/watch?v=dHne2rOYa9U
* https://youtu.be/TPExGCeTdbo?si=Zqv4sbZYx826VPuP
Temas: #Servidores-web #Redes 
### ¿Que es nginx?
Nginx es un servidor web y servidor proxy de alto rendimiento, permite servir contenido a través de los protocolos HTTP y HTTPS. Es muy eficiente a la hora de servir contenido estático, como archivos HTML, CSS, JavaScript e imágenes.
Ademas de sus funcionalidades como servidor web, Nginx puede ser utilizado como:
* **Reverse proxy**: recibe las peticiones de los clientes y las reenvía a servidores o aplicaciones internas
* **Servidor de cache**: almacena temporalmente respuestas para reducir el trabajo del servidor backend y mejorar los tiempos de respuesta.
* **Balanceador de carga**: distribuye las peticiones entre varios servidores de backend
* **Servidores proxy de correo:** puede actuar como proxy para protocolos de correo como IMAP, POP3 y SMTP

![](https://www.muylinux.com/wp-content/uploads/2019/03/NGINX.jpg)

### Alternativas a nginx
Algunas alternativas a nginx son:
* apache
* caddy
* haproxy
* iis

### Proceso de instalación de nginx en linux
```bash
# Instalar nginx
sudo apt install nginx

# Verificar el status del daemon de nginx
sudo systemctl status nginx

# Habilitar nginx para que inicie systemd
sudo systemctl enable nginx

# Iniciar el servicio de nginx
sudo systemctl start nginx
```

### Configuración básica de nginx 
Cuando trabajamos con servidores web como apache o nginx en linux, los sitios web por defecto de estos servidores se alojan en la siguiente ruta.
```bash
cd /var/www/html
```

Creamos un carpeta llamada fútbol dentro del directorio **/var/www**
```bash
sudo mkdir -p devOS/html
```

Dentro de la carpeta html creamos un archivo **index.html** y alli colocamos el codigo frontend de nuestra pagina web.
```bash
sudo vim index.html
```

Dentro del directorio **/etc/nginx**, existen dos directorios
* **sites-availabe**: Directorio en donde colocamos los sitios web listos para producción
* **sites-enabled**: Directorio de producción en donde se encuentran los sitios que ya están disponibles para el publico en general y van a salir si o si.
```bash
cd /etc/nginx
```

Dentro del directorio sites-available creamos el siguiente archivo.
```bash
cd /etc/nginx/sites-available
sudo vim devOS.com.conf
```

```bash
# devOS.com.conf
server {
	listen 80;
	listen [::]:80;
	root /var/www/devOS/html;
	index index.html index.htm;
	server_name devOS.com;
}
```

Una vez hemos creado el archivo el archivo .conf, hacemos un symlink del archivo a **sites-enabled**
```bash
# Revisamos que la sintaxis del archivo sea correcta
sudo nginx -t

# Creamos un symlink del archivo de configuracion
sudo ln -s /etc/nginx/sites-available/devOS.com.conf /etc/nginx/sites-enabled/
```

Ahora reiniciamos el daemon de nginx
```bash
sudo systemctl restart nginx
```

Por ultimo editamos el archivo **/etc/hosts** y colocamos el server_name junto al localhost.
```bash
cat /etc/hosts
127.0.0.1	localhost	devOS.com
```

Ahora si abrimos un navegador podemos escribir devOS.com y nos llevara al sitio web.
```bash
devOS.com
```
### Notas Relacionadas
[[DNS]]


