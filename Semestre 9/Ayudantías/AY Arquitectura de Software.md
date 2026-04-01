# Ayudantía 2
25/03/26

## Requerimientos Funcionales
## Requerimientos NO Funcionales
No ayudan a mejorar, sino que miden si cumplen con atributos necesarios, que si no se cumplen, pueden inutilizar toda la aplicación.

- Performance
- Escalabilidad
- Mantenibilidad
	- Seguridadqsss
- Confiabilidad: Regla de los 5 9 (cinco nueves)
- Integrabilidad
- Portabilidad
- Verificabilidad
- Soportabilidad

## Arquitecturas

- Cliente/Servidor
- Capas
- SOA
- Microservicios

### Cliente/Servidor
El más simple, el cliente pide datos directamente al servidor. Puede ser multicliente 

- [p] Centralización de datos, fácil de mantener
- [c] Punto unico de falla si no se instancian. Cada server es independiente y no comparten datos

EJ) un sistema de cajero automatico. El cajero es el cliente que pide el saldo, y el servidor central del banco responde

### SOA
Evolución del cliente/servidor (bus de servicio)

- [p] Comparte servicios, reutiliza, escalable y mantenible
- [c] Bus único punto de falla. Complejidad

EJ) El sistema interno de una aerolinea. El servicio de reserva que se comunica con el de pagos y el de milla-pasajero, que pueden estar en tecnologías distintas.

### Micro-Servicios
Se expande tanto que son distintos servicios completamente independientes que hacen una sola cosa muy bien. Cada uno tiene su propia base de datos

- [p] Escalabilidad e independencia de servicios
- [c] Altísima complejidad de monitoreo y comunicación

EJ) Netflix. Un micro-servicio se encarga de portadas, otro de recom*Ventaja*ddddxendaciones, cobro, vídeo. Si falla el de recomendaciones, igual puedes ver películas

### Capas
Se puede usar como forma de organizar en secuencia y niveles de abstracción. Describe más la estructura interna del código, complementario

- [p] Modificable fácilmente
- [c] Puede ser lenta (performance) al ir capa por capa

EJ) Una aplicación de escritorio contable. Separa la pantalla donde ingresas números. de las reglas de impuestos y de la base de datos local.


![[Pasted image 20260325144913.png]]


## Ej Control 1

2. “Tal como su nombre lo sugiere, la arquitectura Cliente / Servidor está estructurada por componentes cliente y componentes servidor. El cliente es el encargado de recibir los requerimientos del usuario y redirigirlos hacia su correspondiente proceso servidor. Esto implica que cada cliente debe tener una contraparte que sea servidor, dado que ambos, en conjunto, deben satisfacer un requerimiento del usuario.”

R: FAKE: no necesariamente por cada cliente debe haber una contraparte como servidor

  
# Ayudantia 3
01/04/26

 zx

