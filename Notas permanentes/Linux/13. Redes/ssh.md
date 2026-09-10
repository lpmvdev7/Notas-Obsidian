Tipo: Nota permanente
Fecha: 2026-08-11
Referencias:
* Linux.pdf
Temas:  #Redes #Linux #Secure-shell #Comandos
### ¿Que hace el comando ssh?
El comando ssh es una utilidad de la linea de comandos de linux que nos ayuda a interactuar con la secure shell, permitiéndonos la conexión a dispositivos remotos de forma segura, la ejecución remota de comandos entre muchas otras cosas.

### Uso del comando
Por lo general el comando tiene una sintaxis muy simple
```bash
# Sintaxis general para conectarse de forma segura a un host remoto
ssh username@remote_host
```

>Para ejemplificar este comando tuve que maniobrar algunas cosas con docker con tal de no montar maquinas virtuales completas, menciono esto por que pronto en este vault habra notas sobre docker y como usarlo.

Tenemos dos computadores pertenecientes a dos desarrolladores distintos, pablo es el desarrollador y daniel es el devops, daniel esta enfermo actualmente y en su computadora residen los archivos para subir la ultima version del sitio web de la empresa. Es por esta razon que pablo necesita entrar dentro de la computadora de daniel.
Para ello Pablo utilizara ssh.

```bash
ssh daniel@172.18.0.3
```
![[ssh-connection.excalidraw|1000]]

En algunos casos los administradores de servidor cambiaran el numero de puerto de ssh de 22 a otro numero, debido a esto la sintaxis del comando cambiara indicando el puerto.
```bash
ssh -p 222 daniel@172.18.0.3
```

También podemos ejecutar comandos usando ssh
```bash
ssh daniel@ip 'echo "Este es pablo desde su computadora" > pablo_saluda.txt'
```

Supongamos que somos parte de un equipo de Devops en una empresa. La infraestructura tiene varios servidores y cada entorno utiliza una llave SSH diferente.
En mi computadora tengo lo siguiente:
```bash
~/.ssh/
├── id_ed25519
├── id_ed25519.pub
├── staging.pem
└── production.pem
```
La llave predeterminada que uso para conectarme a los servidores de desarrollo es la llamada **id_ed25519**, pero esta no funciona para autenticarme dentro del servidor de producción, para esos casos tengo la llave llamada **production.pem** que es una llave privada hacia ese servidor.
En esos casos tenemos que usar el siguiente comando de ssh.
```bash
# Proporcionamos una llave 
ssh -i ~/.ssh/production.pem deploy@10.0.20.15
```

### Notas Relacionadas
[[comandos-linux]]
[[ssh-keygen]]
[[ssh-copy-id]]
[[ssh-keyscan]]
[[ssh reenvio de puertos]]
[[Ejemplo completo de comandos ssh]]

