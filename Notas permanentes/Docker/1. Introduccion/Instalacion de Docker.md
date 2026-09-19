Tipo: Nota permanente
Fecha: 2026-09-14
Referencias:
* **[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)**
Temas:  #Docker #Introduccion-Docker 
### Proceso de Instalación de Docker
Cuando hablamos de instalar docker estamos hablando de instalar el docker engine, esta es la tecnología que permite construir y contenerizar nuestras aplicaciones.

### 1. Desinstalar paquetes no oficiales de docker
Lo primero que tenemos que hacer es desinstalar cualquier paquete no oficial relacionado a docker que se encuentre en nuestra maquina.
Para ello la documentación nos brinda el siguiente comando:
```bash
sudo apt remove $(dpkg --get-selections docker.io docker-compose docker-compose-v2 docker-doc docker-buildx podman-docker containerd runc | cut -f1)
```
>Notese la presencia del comando dpkg en el comando proporcionado, esto nos habla de que este comando es solo para distribuciones basadas en debian, tales como ubuntu, mint o zorin os.

### 2. Instalar los paquetes de Docker
La documentación de docker nos brinda la opción de configurar los repositorios APT para agregar los paquetes a las fuentes disponibles para el uso de apt.
Todas esas instrucciones las podemos colocar dentro de un bash script y al ejecutarlo tendríamos docker instalado.
```bash
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update

sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### 3. Comprobar la instalación
El proceso que acabamos de completar instala un daemon, el cual manejara systemd. 
Con esta información podemos comprobar que docker esta correctamente instalado con el siguiente comando.
```bash
sudo systemctl status docker
```

En caso que docker no este ejecutándose podemos hacer los siguiente:
```bash
sudo systemctl start docker
```

Dado que constantemente estaremos ejecutando docker, es algo muy tedioso el depender de los 2 comandos anteriores cuando queramos iniciar nuestro flujo de trabajo con docker, para ello el comando enable nos permite iniciar el servicio de docker automáticamente cada vez que prendamos nuestro equipo.
```bash
sudo systemctl enable docker
```
### Notas Relacionadas
[[systemctl]]
[[dpkg]]
[[Bash Scripting]]

