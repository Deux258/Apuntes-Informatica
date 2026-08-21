# Clase 1
14/08/26


Si queremos comunicarnos entre distintos proveedores, necesitamos puntos de intercambio a través de *protocolos*.

BGP -> Gateway Border Protocol

#### Conectividad resiliente de la UDP
Lo ideal es no depender de una sola conexion, debo asegurar  resiliencia con redundancia para evitar caidas de servicio.

En teoria envio informacion entre 2 servidores para mantener sincronia.

- Para evitar caidas debo tener redundancia con distancia geografica para eitar que se caiga por una sola via

De que forma puedo validar como funciona internet?

*Round robin* -> Se van por distintas rutas

¿Porque banderas de otro pais? 
Porque el prefijo es de x pais, no que geograficamente este en x pais

(Level 3 communications, inc. (GBLX))
Significa que el prefijo es de level 3, comprado por GBLX


#### Sondas Traceroute
Traza de rutas entre un punto y otro

Protocolo -> Da lo mismo, va descontando los TTL

Nic.cl
Lacnig -> Todo latinoamerica
Raid -> Para europa

Tiene distintas sondas por todo el mundo para establecer ip a cada servicio

¿Porque hay latencia?
- No necesariamente por distancia, cantidad de saltos, o tipo de red
- Puede ser por congestion de trafico, mucho ruido


### Caso 1
1. Describan -> ¿Que aparece realmente en la salida
2. Propongan
3. Duden
4. Comprueben

### *Tarea*

> Porque no puedo navegar con prepago

### Caso 2

- Router saturado -> Estoy viendo latencia del enlace del buffer + respuesta (politica de respuesta tirada a cola).
- X Salto de red: No puede ser porque son consecutivos
- X Canal lento porque tambinn seria de arrastre si es que demoro por el canal anterior


### Caso 5
Aparecen direcciones privadas

X Ip Privada de otra infraestructura

- Para que voy a tener ip publica si es que me mantengo en red local?


# Clase 2
18/08/26

### RIPE Atlas
El dispositivo permite medir infraestructura a nivel de red *variaciones fisicas de red*.
Herramientas de ping, nodos, ver latencia, resoluciones, etc

-  *Looking Glass* -> Los servidores los tienen - puntos de observacion de la red (ej VM)
- *Traceroute* -> Herramienta más usada pero es la peor para análisis

Clients -> Internet -> Load Balancer -> Servers

EJ) 30 hops max
- Con 30 saltos debiese llegar a cualquier nodo/parte del mundo.
- Puedo diferenciar distintos tipos de TTL (32, 128, 64, 32 (no muy visto)).
- Si no tengo conectividad, no voy a iterar al infinito (indicar limite)

- Son 3 paquetes por TTL (distintas vias) para *maximizar respuesta*
	- Se ve mucho en protocolos como DNS, basados en UDP

117-114 o 110?
*Depende* -> Necesito mas muestras 

>EJEMPLO
- Protocolo por defecto TCP es UDP
Va desde un puerto random hasta un puerto secuencial que va desde $2^{15}+666$ (33434)
- Las erespuestas son en ICMP

### Desafios de Traceroute

- No siempre muestra la ruta exacta que siguen los datos
- Puede ser afectado por el balanceo de carga
- Puede ser bloqueado o alterado por iteracion
- *Tengo que sacar varias mediciones* para sacar conclusiones

- **SOLO** sirve para mostrar *que rutas tomaron* / nodos tomaron

### Scamper - Trace
Software que si se sigue actualizando - Desarrollado por caida
Monogable con traceroute (puede dar el mismo resultado)

*Tracelb* -> Load Balancing
Diferencia es que me dice el enlace que sigue (este con otro)

Para una red, para que uso  broadcast? (Mascara /30)
-> /31 no tiene para broadcast
-> 

### Scamper Warts 
Scamper pero en formato json 

### RESUMEN
- Traceroute sirve para un comienzo pero NO para topología.
 

# Clase 3

## Paper a Realizar
Usar api para obtener metadata. Contexto de drones - La idea es buscar algun paper 

Para la prox clase tener los grupos conformados

Basicamente buscar la mejor ruta para un dron en x contexto
Por ej: Operaciones militares, incendios forestales, etc

- Parecido a tics 1
- Que sea api que de verdad me de informacion
- Agarrarse de un paper para nutrirlo con un contexto
- No necesariamente chilena, puede ser global

## Metadata

Extracción de datos del entorno - Permite categorizar de mejor forma nuestros intereses. 

- Necesitamos saber donde esta ubicada la topologia y que amenazas pueden existir para evitar fallas a futuro.
- Amenazas: Metadata dentro del sistema, pero *no está todo el tiempo*

### Scamper
Podemos hacer una traza pero sólo tenemos IPs.

Baf -> Banda ancha fija
Para maquinas que funcionan 24/7


![[{6AFAE02D-AD31-47CA-A721-C1EEEE76A5B0}.png]]

- Destinos con quien ha tenido conectividad
- Tuvo ataques de MSSQL Login y SMBvl Crawler
- Un atacante puede suplir una ip

Los buscadores que existian no eran especializados en buscar informacion de redes sino indexar paginas web.

>La idea es que tanto puedo obtener de una ip para mi traceroute

- **Censys** App para buscar ips disponibles 
- **ZoomEy**:

![[{80DCE44E-31BF-4EBC-A210-61A5A6111C9A}.png]]

Entrega incluso cual es el servidor web que usa (de ahi que saca que es ubuntu). 
>La info se entrega en codigo apache, si lo modifico puedo colocar cualquier otra cosa

Desde un punto en particular podria mapear toda la red, tanto la interna como la externa. *Buen inicio para auditoria de red*

A traves de la ip puedo saber a que entidad pertenece, por ej UDP, incluso sabiendo la localizacion de donde se conecta la red


#### IP2Location
![[{1649A7E7-5859-48A3-9930-6DEDD367E758}.png]]

![[{8FFE2924-D721-44BE-B763-F0737F001946}.png]]

Sabemos que tenemos que usar info del contexto, y saber buscar apis.
Google no sirve para esto, el que si por ej es **RAPID API**

> NO TODA LA INFO ESTA ACTUALIZADA

### Shodan Search Engine
Por tener mail udp, tenemos mucho mas acceso que la cuenta gratis.
Podemos ver hasta exploids y vulnerabilidades

### Vulners 
Buscador para vulnerabilidades de ciertas ips en X rango de tiempo

![[{D854E924-813A-468D-8A09-1B46B79625E1}.png]]

Debieramos decir que podemos modificar el software/codigo fuente para que en wireshark se vea otro tipo de servidor.

- !! No todo servicio es fiable - En qué confio?
- A partir de una unica ip podemos saber las vulnerabilidades, ubicacion, quien es el responsable


## Ruteo / Resiliencia para UAV

Levantar info con respecto a una problematica donde se aplique ruteo para x amenaza en drones. Ahi es donde entra la metadata para recopilar informacion, 

![[{74432757-8538-448E-9F78-A6323D10CF7B}.png]]


- EJ) La distancia o seguridad es mi problema principal?

- Hay una api para conocer la altura de los edificios y sus tipos 
- 

### Papers
Buscar a traves de keys (por ej risk uav path)
La idea es colocar el algoritmo realizado en un dron para poder jugar con el

https://scholar.google.com/?hl=es
https://ieeexplore.ieee.org/Xplore/home.jsp
https://www.elsevier.com/es-mx !! con problemitas

https://sci-hub.box/ Con url para buscar 