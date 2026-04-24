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

EJ) Netflix. Un micro-servicio se encarga de portadas, otro de recompensas 
*Ventaja*ddddxendaciones, cobro, vídeo. Si falla el de recomendaciones, igual puedes ver películas

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


# Ayudantía 4 - Solemne 1
15/04/26

## 1 . Selección Múltiple


1. Sobre la naturaleza de los Requerimientos No Funcionales (RNF) y los Atributos de
Calidad, ¿cuál de las siguientes afirmaciones es técnicamente precisa?

a) Los RNF ayudan a mejorar directamente las funciones del sistema, incrementando su
calidad estética. 
b) Un arquitecto debe incluir la mayor cantidad de RNF posibles, ya que mientras más haya,
mejor será el comportamiento. 
c) Si dos RNF definidos por el arquitecto se contradicen lógicamente, no es un problema de
la arquitectura, sino un error de especificación del documento. 
d) Los atributos de calidad son opcionales y no influyen en si una aplicación es útil o queda
inutilizada. 

a) RNF explica cómo lo hace
b) RNF tienen trade-offs, incluir demasiados puede hacer el proyecto inviable
*c)* El arquitecto debe negociarlas, pero el error de origen es del documento
d) Un sistema lento o inseguro queda inutilizable aunque "funcione"


2. En el contexto de los Atributos de Calidad y sus tácticas de mejora, identifique la
relación correcta:

a) La Escalabilidad Vertical consiste en crear más instancias activas de servidores para
distribuir el tráfico. *F*
b) Para mejorar la Confiabilidad, una táctica clave es eliminar puntos únicos de falla y
producir instancias en distintas geografías. *TRUE*
c) El 'No Repudio' es un pilar de la Performance que mide el tiempo de respuesta ante un
estímulo. *FAKE*
d) La Verificabilidad se logra exclusivamente mediante la creación de logs y monitoreo de
métricas post-incidente.

a) Fake: Describe la escalabilidad horizontal
b) True
c) Fake: No repudio: garantizar que alguien no pueda negar una acción
d) Fake: el testeo se facilita desde el diseño, no solo con logs


3. Respecto a la arquitectura Cliente/Servidor y su funcionamiento, señale la opción
correcta:

a) En este modelo, el cliente debe conocer la ubicación física y la implementación interna
del servidor para concretar la comunicación. *FAKE*
b) Es una arquitectura donde los componentes se agrupan en capas según los
componentes más demandados por el usuario. *FAKE*
c) El servidor se considera un punto único de falla (SPOF) debido a su estructura
centralizada si no se implementan medidas de redundancia. *TRUE*
d) Es la evolución máxima de SOA, donde se divide la aplicación en servicios minúsculos
con bases de datos propias *FAKE*

a) Fake: No es necesario conocer la ubicación física ni la implementación interna
b) Esa es la arquitectura de capas, no cliente/servidor
c) True
d) Arquitectura SOA


4. Sobre el rol del Arquitecto de Software y su distinción con la Ingeniería de
Software:

a) El arquitecto es el responsable principal de la administración del equipo de desarrollo y la
interfaz con el usuario. *FAKE*
b) La ingeniería de software se enfoca únicamente en las decisiones de diseño que son
difíciles de cambiar. *FAKE*
c) El arquitecto se enfoca en cómo se dividen las responsabilidades del sistema (módulos) y
cómo interactúan para garantizar atributos como escalabilidad o seguridad. *TRUE*
d) El rol del arquitecto es garantizar que el sistema cumpla con los requerimientos
funcionales y algoritmos detallados de cada proceso. *FAKE*

El ingeniero de software abarca todo el ciclo de vida desde la captura de requisitos hasta el término de ejecución del software, enfocándose en la eficiencia del proceso de creación.


## 2. Análisis de V/F (justificar)

1. Frase: "Para lograr el desacoplamiento total en una arquitectura de Microservicios,
es fundamental que todos los servicios consulten una única base de datos
centralizada."

R: FAKE: Es uno de los mayores antipatrones en microservicios. Genera un acoplamiento a nivel de datos, si cambio el esquema de una tabla, puede romper al resto


2. Frase: "En una arquitectura SOA (Service Oriented Architecture), el Bus de
Servicios (ESB) actúa como intermediario, eliminando por completo los cuellos de
botella y los puntos críticos de falla."

R: FAKE: Aunque el bus SOA permite la comunicacion entre componentes distintos, en realidad el bus seria el unico punto de falla (SPOF).

3. Frase: "El Modelo de Repositorio (Data-Centric) permite una alta flexibilidad para
modificar el esquema de la base de datos sin afectar a los componentes clientes."

R: 

4. Frase: "Una arquitectura Cloud-Native aprovecha la elasticidad para ajustar la
capacidad de cómputo de forma dinámica, eliminando la necesidad de planificar la
capacidad máxima teórica."

R: Verdadero


5. Frase: "En el diseño de Microservicios, si un servicio como el de 'Recomendaciones'
falla, la arquitectura puede tener problemas de comunicación con servicios
relacionados a este."

R: FAKE: Porque los microservicios no se relacionan entre sí a diferencia de SOA. La idea es que sean lo más independientes posibles.


