Tipo: Nota permanente
Fecha: 2026-08-18
Referencias:
* 
Temas: #DNS 
### Problema
Tenemos dos contenedores Ubuntu en la misma red Docker:
```bash
dns-server -> 172.18.0.3
app-server -> 172.18.0.2
```

Nuestro trabajo es configurar BIND9 en **dns-server** para crear la zona:
```bash
lab.local
```

Debes conseguir que:
```
dns.lab.local -> 172.18.0.0
app.lab.local -> 172.18.0.2
```

Ademas, configura la zona inversa para que:
```bash
172.18.0.2 -> app.lab.local
172.18.0.3 -> dns.lab.local
```

En **dns-server**:
* Configura named.conf.local
* Crea la zona directa
* Crea la zona inversa.
* Usa Registros A, PTR, SOA y NS
* Valida todo con named-checkconf y named-checkzone

En app-server:
* Configura su DNS para que utilice 172.18.0.3

### Solucion
En ambas maquinas de docker nos aseguramos de instalar bind9
```bash
sudo apt install bind9 dnsutils -y
```

Modificamos el archivo named.conf.local en el server 1
```bash
# /etc/bind/named.conf.local
zone "lab.local"{
	type master;
	file "/etc/bind/zones/lab.local-direct.conf";
};

zone "0.18.172.in-addr.arpa"{
	type master;
	file "/etc/bind/zones/lab.local-reverse.conf";
};
```

Despues procedemos a crear un directorio zones dentro de /etc/bind
```bash
mkdir zones
```

Copiamos el contenido del archivo db.local, esto con el objetivo de usarlo como plantilla para nuestros archivos de configuración de zona directa e inversa.
```
cp /etc/bind/db.local /etc/bind/zones/lab.local-direct.conf
cp /etc/bind/db.local /etc/bind/zones/lab.local-reverse.conf
```

Una vez tenemos creadas nuestras plantillas procedemos a editarlas.
Primero editaremos la zona directa.
```bash
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	dns.lab.local. admin.lab.local. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
; Registros DNS

@	IN	NS	dns.lab.local.
dns	IN	A	172.18.0.3
app	IN	A	172.18.0.2

```

Después la zona indirecta
```bash
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	dns.lab.local. admin.lab.local. (
			      2		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	dns.lab.local.
3	IN	PTR	dns.lab.local.
2	IN	PTR	app.lab.local.

```

Para este punto ya hemos modificado 3 archivos de configuración, los siguientes comandos nos ayudaran a verificar que no tengamos errores en la sintaxis.
```bash
sudo named-checkconf # Verifica la validez de named.conf.local
sudo named-checkzone # Verfica la valides de los archivos de configuracion de zonas
```

Ahora nos aseguramos de reiniciar el servicio de named en el contenedor.
```
service named restart 
service named staus
```

Por ultimo en modificamos /etc/resolv.conf agregando la siguiente linea:
```bash
nameserver 172.18.0.3
```

Ahora nos dirigimos a lab-server2 y modificamos /etc/resolv.conv agregando la misma linea de la instrucción anterior.
```bash
nameserver 172.18.0.3
```

Utilizando el comando nslookup verificamos que el servidor DNS que acabamos de configurar funcione correctamente.
```bash
root@server2:/# nslookup 172.18.0.3
3.0.18.172.in-addr.arpa	name = dns.lab.local.

root@server2:/# nslookup 172.18.0.2
2.0.18.172.in-addr.arpa	name = app.lab.local.

root@server2:/# nslookup dns.lab.local
Server:		172.18.0.3
Address:	172.18.0.3#53

Name:	dns.lab.local
Address: 172.18.0.3

root@server2:/# nslookup app.lab.local
Server:		172.18.0.3
Address:	172.18.0.3#53

Name:	app.lab.local
Address: 172.18.0.2
```

Un servidor DNS nos permite olvidarnos de las direcciones ip dentro de una red y poder hacer cosas como estas.
```bash
# Hacer ping a otras maquinas
ping dns.lab.local

# Copiar llaves ssh a otras maquinas
ssh-copy-id pueblo@app.lab.local

# Entrar a otras maquinas mediante ssh
ssh pueblo@app.lab.local

```
### Notas Relacionadas
[[DNS]]
[[BIND9]]
[[nginx]]

