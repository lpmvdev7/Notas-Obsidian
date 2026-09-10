Tipo: Nota permanente
Fecha: 2026-08-18
Referencias:
* https://www.youtube.com/watch?v=l-ZuM4yqoIk
Temas: #DNS 
### ¿Que es BIND9?
BIND9 es un programa que nos permite la configuración de DNS en linux.

### Instalación
```bash
sudo apt install bind9 dnsutils -y
```

### Configuración DNS
#### Ver nuestra dirección IP
Lo primero que tenemos que hacer es verificar nuestra dirección IP
```bash
ip a 
# 192.168.1.101
```

#### Entramos a la carpeta de bind
Nos dirigimos a la carpeta de bind
```bash
cd /etc/bind
```

En esta carpeta se encuentran los archivos de configuración para el servidor DNS.
```bash
bind.keys
db.0
db.127
db.255
db.empty
db.local
named.conf 
named.conf.default-zones
named.conf.local
named.conf.options
rndc.key
zones.rfc1918
```

#### Creación de zonas
Abrimos el archivo **named.conf.local** con vim o nano y lo configuramos de la siguiente manera.
```bash
cat named.conf.local 
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

# Configuracion DNS directo
zone "lpmvdev7.com" {
	type master;
	file "/etc/bind/db.lpmvdev7.directa.com";
};

# Configuracion DNS inverso
zone "1.168.192.in-addr.arpa" {
	type master;
	file "/etc/bind/db.lpmvdev7.inversa";
};
```

Debido a que los archivos de configuración de la zona directa e indirecta no existen aun, procederemos a crearlos, para ello copiare db.local para usarlo como plantilla.
```bash
sudo cp db.local /etc/bind/db.lpmvdev7.directa.com
sudo cp db.local /etc/bind/db.lpmvdev7.inversa

# Contenido de db.local
cat db.local 
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	localhost. root.localhost. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	localhost.
@	IN	A	127.0.0.1
@	IN	AAAA	::1

```

Editamos el archivo de zona directa
```
sudo vim /etc/bind/db.lpmvdev7.directa.com
```

```bash
; Archivo de zona directa
# @ = lpmvdev7.com
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	ns1.lpmvdev7.com. admin.lpmvdev7.com. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;

@	IN	NS 	ns1.lpmvdev7.com.

ns1	IN	A	192.168.1.101
www	IN	A	192.168.1.101
```

Editamos el archivo de zona indirecta
```bash
sudo vim /etc/bind/db.lpmvdev7.inversa
```

```bash
; Archivo de zona indirecta
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	ns1.lpmvdev7.com. admin.lpmvdev7.com. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns1.lpmvdev7.com.
101	IN	PTR	ns1.lpmvdev7.com.
```

Verificamos que la sintaxis de nuestros archivos de configuración este correcta
```bash
sudo named-checkconf
```

Verificamos que la sintaxis de configuración de nuestras zonas sea correcta.
```bash
# Zona directa
named-checkzone lpmvdev7.com /etc/bind/db.lpmvdev7.directa.com

# Zona inversa
named-checkzone 1.168.192.in-addr.arpa /etc/bind/db.lpmvdev7.inversa 
```

Reiniciamos el servicio llamado named
```bash
sudo systemctl restart named
sudo systemctl enable named
```

Por ultimo editamos resolv.conf comentando la linea nameserver y agregando esta otra:
```bash
nameserver 192.168.1.101
```

>NOTA:  el archivo resolv.conf se actualiza automáticamente cada vez que volvemos a encender el computador, si queremos evitar este comportamiento tenemos que crear un archivo llamado **90-dns-none.conf** en **/etc/resolv.conf** y dentro de el colocar la siguiente instrucción:
```bash
[main]
dns=none
```

### Notas Relacionadas
[[DNS]]
[[Ejercicio de configuracion DNS con BIND9]]
