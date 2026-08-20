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
 










