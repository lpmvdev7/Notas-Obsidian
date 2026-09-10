Tipo: Nota permanente
Fecha: 2026-08-11
Referencias:
* Linux.odf
Temas: 
### ¿Que es secure shell?
Secure shell es un protocolo de red criptografica diseñado para la comunicación segura a través de una red que no es segura.
SSH es ampliamente utilizado para inicio de sesión remoto entre sistemas, la ejecucion de comandos de forma remota, la transferencia de datos entre equipos de computo y muchos usos mas. SSH es el estándar actual de la industria para comunicar servidores dentro de redes no seguras de forma segura.

En distribuciones basadas en Debian, que utilizan el gestor de paquetes apt, utilizamos el siguiente comando para instalar ssh.
```bash
sudo apt install openssh-server
```

Esto instalara el daemon sshd, por lo que la configuración de ssh se encontrara disponible en la siguiente ruta de archivo
```bash
cat /etc/sshd_config
```

### Notas Relacionadas
[[ssh]]



