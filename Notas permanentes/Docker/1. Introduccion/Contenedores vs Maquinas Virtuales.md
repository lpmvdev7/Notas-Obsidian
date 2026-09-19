Tipo: Nota permanente
Fecha: 2026-09-15
Referencias:
* https://www.youtube.com/watch?v=eyNBf1sqdBQ
Temas: #Contenedores #Docker #Maquinas-Virtuales
### ¿Que es una Maquina virtual?
Una maquina virtual yo la entiendo como una computadora pequeña, esta computadora pequeña contiene todo lo que necesita un computador normal para funcionar, un sistema operativo, memoria CPU y memoria RAM, con la particularidad que todo esto se encuentra virtualizado usando una capa de software llamada hypervisor, esta capa de software permite la virtualizacion del hardware fisico del host al hardware virtual que necesita una maquina virtual para funcionar.
Una maquina virtual en si es una mini computadora que vive dentro de nuestro computador principal.
![](https://upload.wikimedia.org/wikipedia/commons/1/16/QEMU_emulator_version_7.2.13_en_Debian_12.7.png?utm_source=es.wikipedia.org&utm_campaign=index&utm_content=original)

### Maquinas Virtuales vs Contenedores
A simple vista pareciera que las maquinas virtuales resuelven el mismo problema que los contenedores, y pues la verdad es que si pero teniendo un detalle muy importante en cuenta: Los contenedores nacen como una alternativa mas portable a las maquinas virtuales, mientras que la maquinas virtuales, valga la redundancia virtualizan un sistema operativo entero, los contenedores toman aquellas piezas minimas que necesita un software para funcionar y utilizando eso para crear copias portables diseñadas para consumir la menor cantidad de recursos posibles.

#### ¿Se pueden usar maquinas virtuales y contenedores a la vez?
La respuesta es SI, ninguna tecnología excluye a la otra, como ya sabemos, los contenedores sirven como paquetes que encapsulan todo lo que necesita un software para funcionar, estos al ser mucho mas pequeños que las VM, pueden vivir dentro de ellas. De esta forma podemos crear ecosistemas empresariales complejos en los que designamos cierto grupo de maquinas virtuales para alojar varios contenedores.
Un ejemplo claro de esta simbiosis ente contenedores y maquinas virtuales son los ecosistemas modernos de nube.
Amazon a medida que fue creciendo empezó a notar que mucha de la capacidad de sus servidores quedaba inutilizada, en ese momento es cuando vieron la oportunidad de vender esa infraestructura mediante un modelo de pago por uso, con esto en mente la idea central de la infraestructura en la nube es un monton de servidores que utilizan hypervisores para virtualizar maquinas virtuales con diferentes sistemas operativos como Ubuntu, Red Hat, entre otros, de esta manera nace la internet moderna en la que desarrolladores de aplicaciones despliegan sus sistemas en estos ecosistemas permitiendo que los usuarios comunes puedan acceder a ellos.

![](https://www.almeritek.com/wp-content/uploads/2019/08/acloud.png)

### Notas Relacionadas
[[About - Docker]]
[[Nube]]

