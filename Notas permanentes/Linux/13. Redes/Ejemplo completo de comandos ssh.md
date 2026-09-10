Tipo: Nota permanente
Fecha: 2026-08-12
Referencias:
* 
Temas: #Secure-shell 
### Sobre el ejemplo
Esta nota tiene como propósito documentar el proceso completo de solución de un ejemplo relacionado al uso de comandos ssh como ssh, ssh-keygen y ssh-copy-id en entornos profesionales.

### Problemática
Trabajas como DevOps Junior en una empresa llamada AcmeTech.
La empresa acaba de crear un nuevo servidor de producción.
```bash
Servidor: production-01
IP: 172.18.0.2
Usuario: deploy
```

El servidor tiene instalado OpenSSH Server y esta configurado para aceptar autenticacion mediante claves SSH.
Tu computadora de trabajo actualmente no tiene ninguna clave SSH destinada a este servidor.
El administrador nos pide que preparemos nuestro acceso.

#### Problemática 1
El administrador nos dice:
>Necesito que generes una nueva identidad SSH exclusivamente para administrar **production-01**. No quiero que reutilices tu clave personal de Github ni ninguna otra clave que tengas.

#### Problemática 2
El administrador nos proporciona una contraseña temporal para conectarnos al servidor y nos menciona lo siguiente:
>Utiliza esa autenticacion inicial para instalar tu clave publica en el servidor. Despues por motivos de seguridad cambiare esa contraseña.

### Problemática 3
Entra al servidor sin utilizar la contraseña.

#### Problemática 4
Después de unos meses nuestra computadora tiene varias claves:
```bash
~/.ssh/
├── id_ed25519
├── github
├── acmetech-staging
├── acmetech-production
└── cliente-x
```

Queremos entrar de nuevo al servidor **production-01** pero nos queremos asegurar que SSH utilice específicamente la identidad de producción, independientemente de las demás claves que tengas.

### Solución
```bash
# Problematica 1
ssh-keygen -t rsa -b 4096 -C "production-01" -f ~/.ssh/acmetech-production

# Problematica 2
ssh-copy-id -i ~/.ssh/acmetech-production.pub deploy@172.18.0.2

# Problematica 3
ssh deploy@172.18.0.2

# Problematica 4
ssh -i ~/.ssh/acmetech-production deploy@172.18.0.2

```


### Notas Relacionadas
[[ssh]]
[[ssh-keygen]]
[[ssh-copy-id]]
[[ssh-keyscan]]
[[secure shell]]

