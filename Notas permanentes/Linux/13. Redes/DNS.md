Tipo: Nota permanente
Fecha: 2026-08-17
Referencias:
* https://www.youtube.com/watch?v=NiQTs9DbtW4&t=226s
Temas: #DNS #Redes 
### ¿Que es DNS?
DNS son las siglas de Domain Name System.
DNS sirve como el directorio telefónico de Internet, las personas no se graban ips complejas para acceder a sus sitios web favoritos, en cambio acceden a ellos mediante nombres de dominio como www.youtube.com.
El DNS traduce los nombres de dominio a direcciones IP para que los navegadores puedan cargar los recursos de Internet.

### ¿Que es un Dominio?
Conjunto de equipos que tienen una administración en común.
```bash
# Los nombres de dominio comparten la siguiente estructura
subdominio.sld.tld

# Por ejemplo
www.google.com
linux.computador.com
```

### ¿Como funciona DNS?
1. Queremos visitar el sitio web www.youtube.com, es la primera vez que lo visitamos.
2. En la direccion web www.youtube.com podemos ver la siguiente estructura en la url:
	1. El subdominio --> www
	2. El SLD (Second Level Domain) --> youtube
	3. El TLD (Top Level Domain) --> .com
3. Escribimos www.youtube.com y el computador verifica el cache local para saber si ya conoce la ip del sitio que queremos visitar.
4. Si el cache local no conoce la ip, se dirige al servidor DNS de Google 8.8.8.8 para ver si este conoce la ip.
5. Si 8.8.8.8 no conoce la ip, entonces consultamos a los roots.
6. Los roots no conocen la ip pero conocen a los TLDS (Top Level Domain Servers), asi que redirigen la consulta según el final del dominio .com, .net, etc.
7. Como el dominio que queremos visitar termina en .com, se consulta a un servidor TLD de .com
8. El TLDS responde indicando donde se encuentra el servidor DNS del SLD (Second Level Domain).
9. En el servidor SLD consultamos un zone file que contiene la ip de www.youtube.com.
10. Una vez encontrada la ip, se conecta al sitio web y estamos dentro.
![[DNS-explained.png]]

### Notas Relacionadas
[[nginx]]
[[BIND9]]


