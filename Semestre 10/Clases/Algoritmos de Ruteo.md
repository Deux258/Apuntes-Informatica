# Clase 1
14/08/26

## 

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
- 