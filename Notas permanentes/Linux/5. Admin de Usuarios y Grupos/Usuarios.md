Tipo: Nota permanente
Fecha: 2026-07-21
Referencias:
* Linux.pdf
Temas: #usuarios #Linux 
### ¿Que es un Usuario?
Un usuario en linux es cualquier persona que tenga acceso a los directorios, archivos y software del computador.

### Tipos de Usuarios
Existen  2 tipos de usuarios principales en linux, estos son:
1. System User: Usuario creado automaticamente cuando se instala el sistema operativo, se encarga de ejecutar servicios y procesos en el sistema operativo.
2. Normal User: Usuario creado por el administrador del sistema, utilizado por personas para ejecutar sus tareas dentro del sistema.

### Comandos para usuarios en Linux
* **useradd**
* **users**
* **userdel**
* **usermod**
* **who**
* **passwd**

### El archivo passwd
El archivo passwd ubicado en /etc/passwd guarda la información de un usuario, este archivo esta compuesto por varias lineas, cada una de las lineas es una usuario diferente, cuya información se guarda con la siguiente sintaxis.
```bash
username:encryptedpassword:userid:groupid:userinfo:homeDirectory:shell
```
El principal uso que yo le doy a este archivo es para verificar que un usuario que yo he creado realmente exista en mi sistema.

### Notas Relacionadas
[[useradd]]
[[userdel]]
[[usermod]]
[[who]]
[[passwd]]