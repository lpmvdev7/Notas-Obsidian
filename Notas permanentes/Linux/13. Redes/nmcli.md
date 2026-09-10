Tipo: Nota permanente
Fecha: 2026-08-10
Referencias:
* https://www.youtube.com/watch?v=NqBpyxUTSyk
Temas: #Redes #Linux #CLi
### ¿Que es nmcli?
nmcli es una interfaz de linea de comandos que interactua directamente con el dameon networkd, este daemon, en sistemas linux, es el encargado de administrar las conexiones de red, por lo que nmcli es la herramienta con la cual podemos gestionar ese servicio de manera mas eficaz.

### Uso de la CLI 
Cuando trabajamos con CLI, y con comandos en general podemos utilizar **--help** despues de la instruccion que queremos utilizar, esto no dara una serie de opciones con todas las operaciones que podemos hacer con dicha palabra reservada.
```bash
nmcli --help
Uso: nmcli [OPCIONES] OBJETO { COMANDO | help }

OPCIONES
  -a, --ask                                solicitar parámetros ausentes
  -c, --colors auto|yes|no                 indica si usar colores en la salida
  -e, --escape yes|no                      escapar separadores de columnas en valores
  -f, --fields <campo,...>|all|common      especificar campos en la salida
  -g, --get-values <campo,...>|all|common  atajo para -m tabular -t -f
  -h, --help                               muestra esta ayuda
  -m, --mode tabular|multiline             modo de salida
  -o, --overview                           modo resumen
  -p, --pretty                             salida suficiente
  -s, --show-secrets                       permitir mostrar contraseñas
  -t, --terse                              salida moderada
  -v, --version                            mostrar la versión del programa
  -w, --wait <segundos>                    establecer tiempo de espera para terminar las operaciones

OBJETO
  g[eneral]       estado general y operaciones de NetworkManager
  n[etworking]    control de red general
  r[adio]         interruptores de radio de NetworkManager
  c[onnection]    conexiones de NetworkManager
  d[evice]        dispositivos administrados por NetworkManager
  a[gent]         agente secreto o agente polkit de NetworkManager
  m[onitor]       monitor de cambios de NetworkManager

```

Una vez visto el tip anterior a continuación paso a detallar algunos usos que le encontré al comando.

Aquí mostramos algunos usos para ver el estado de la red, las interfaces y las conexiones de red.
```bash
# Ver el estado de la red en general
nmcli general status 
```

```bash
# Muestra los detalles de los dispositivos de red.
nmcli device show

# Aqui mostramos los detalles de la interfaz de wifi
nmcli device show wlp0s20f3
```

```bash
# Nos muestra todas aquellas redes a las que nos hemos conectado alguna vez
nmcli connection show
```

```bash
# Nos muestras todas aquellas redes que se encuentran activas ahora mismo
nmcli connection show --help
```

Interactuando con el wifi a través de nmcli.
```bash
# Encender el wifi a traves de la terminal
nmcli radio wifi on

# Apagar el wifi a traves de la terminal
nmcli radio wifi off

# Listar las redes wifi disponibles
nmcli device wifi list
```

Desconexion total de red
```bash
# Apagar la red 
nmcli networking off

# Encender la red
nmcli networking on
```

En mi humilde opinión considero que este es el comando mas completo relacionado a redes que me he encontrado en linux, es una utilidad muy completa la cual considero que cualquiera que pruebe linux para trabajos en desarrollo o devops debería conocer.

### Caso de uso del comando
Somos administradores de un servidor Linux y un usuario reporta que no tiene conexión a Internet. Al revisar físicamente el equipo, la tarjeta de red esta conectada correctamente, pero no sabemos si el problema esta relacionado con la interfaz de red, la conexión configurada o el estado de NetworkManager.
Nuestra tarea es:
* Identificar las interfaces de red disponibles 
* Comprobar cuales están activas
* Revisar las conexiones de red configuradas
* Determinar cual conexión esta actualmente activa
```bash
# Identificar las interfaces de red disponibles
nmcli device show

# Comprobar cuales estan activas
nmcli device status

# Revisar las conexiones de red configuradas
nmcli connection show

# Determinar cual conexion esta actualmente activa
nmcli connection show --active

```

### Notas Relacionadas
[[CLI]]
[[comandos-linux]]
[[Servicios linux]]
[[resolvectl]]
