
# Clase 1 
09/03/26

## Intro
El término fue inventado en 1999

Lo *smart* viene en la capacidad de interconexión y en el intercambio de datos que hagas con los demás objetos, un solo tipo de red para todo
- *Smart Object* no implica inteligencia

habian 2 problemas principales:
1. La forma de transmitir info (paquets con datos)
2. Seguridad y privacidad
   
- No todas las tecnologias se incorporan masivamente de un dia para otro

- ¿Existe la portabilidad entre ciertos servicios?
	Debería, pero no existe por la competencia entre empresas

- Interfaz inalámbrica: Wifi, Buetooth, datos móviles

la idea de un estándar es mantener unidad entre empresas para una misma "herramienta", que mantengan a sus usuarios no por las capacidades, sino por su "conveniencia"

##### ¿Qué cosas califica como IoT?

- Un celular *NO* califica como *IoT*
- Un mouse podría serlo
- Aire acondicionado  *SI* es *IoT*, comunica temperatura (1 parámetro)

- **Personalidad**
	- Pueden ser *fuentes de informacion*: sensores
	- o *Destinos* y ser actuadores

En un sistema orientado al cloud computing exclusivamente, se toman de *forma jerárquica*
- La energía es fundamental

Pero un sistema donde los nodos se conectan entre ellos
	Se denomina *Fog computing* (intermedio), parte del concepto de Internet of Everithing

1. Instalado en la infraestructura
2. Covertura por redes inalámbricas
3. Usando de manera satelital

### Redes tradicionales
- Estaciones base conectadasa a un *backbone*
- Elementos móviles conectados de manera inalámbrica a la estación base

### Redes de Nodos sensores (a estudiar)
Red de nodos con sensores comunicándose entre sí sin tener que usar servicio de nadie

- Multisalto
- Solo un salto
- Puente para otras redes
- Gateways simples o multiples
- Topologías Mesh / Estrella / Árbol

Una métrica es *tiempo de vida de red* para medir la eficacia de una red
La existencia de caminos alternativos es buena (like)

Una cosa es la topología, y otra es la red que armamos encima de este, usara parte de la topologia disponible para comunicar. Uso sólo los convenientes 
	¿Estan todos disponibles? Si
	¿Debería usar todos? No

## Características de Nodos

1. Corto alcance (50-100m) o Largo alcance con limitaciones grandes 
2. Poca capacidad de procesamiento 
	Buscamos el mínimo hardware para hacer lo mismo, ser eficiente es mejor
3. Alimentados a Batería 
	TX, RX, Sensor
4. Poca capacidad de Almacenamiento
	 Tablas limitadas, tamaño del programa, registro limitado 
5. Relojes de baja precisión
	Sincronización (muy importante), compensación
6. Tamaño
	Acceso, Ubicación, Peso, Gabinetes estandarizados, Antenas o Mantenibilidad
7. Interfaces de programación y comunicación
	Conectores, estándares
8. Sistemas Operativos, Stacks, Lenguajes de programación
	Disponibilidad
9. Robusto físicamente
	Ambiente hostil: vibraciones, temperatura, químicos..
10. Auto-Organizarse
	Construcción de rutas, intercambio de claves, estabilidad
11. Sincronización
	Sistemas TDMA (time division multiple access) o Híbridos CSMA/TDMA
12. Mantener bajo consumo
	Duración de batería
13. Redundancia
		Lograr recuperarse de fallas de nodos (Redundancia de topografía, reconstrucción de vias)
14. Seguridad
    Encriptación en capas, distribución de claves
15. Incluir Identificación, autentificación
16. Proveer localización 
	Para georeferenciación y/o asignación de recursos


## Problemas

Si uno no tiene registro de errores o de lo que está pasando, uno no puede hacer mucho para solucionar.

1. Control de Acceso
2. Enrutamiento
3. Topología
4. Recursos
5. Consumo
6. Gestión
7. Transporte de Datos
8. Movilidad
9. Regulación
	Ancho de banda, potencia, Canalización, Zonas

## Datos

Patrones de funcionamiento

-  Envío *periódico* de datos
- Detección de *Eventos*	
- Aproximación de funciones
	Puedo hacer un conjunto de mensajes de distintos sensores y transmitirlo como uno
- Detección de bordes
	Pregunto cuando hay algún cambio
- Seguimiento de objetos
- Consultas a la red
- Pre-procesamiento en la red
- Redes orientas a contenidos
- ¿Tiempo real? -> Garantías de Máximo retardo y Pérdida de datos

*Priorización* de información a mandar es crucial también

## ¿Cómo se distribuyen los Nodos?

1. Al azar (Lanzados desde un dron, avión)
2. Regularmente (Matricial)
3. De acuerdo a la *representavilidad de la variable* a medir (densidad variable)
4. Móviles (movimiento)
	Patrones regulares o irregulares de movimiento, movidos por una fuente externa por ej flujo de agua o petróleo

## Mantenimiento y Escalabilidad

### Mantenimiento

- Reemplazo de Baterías posible?
- Alimentación a partir de fuentes externas
	Sol, movimiento, vibraciones
- Duración esperada
- Detección de fallas
- Incorporación de nuevos nodos durante el funcionamiento de la red
- Contaminación posible

### Escalabilidad

- Limitaciones en direccionamiento/enrutamiento
- Limitaciones de recursos disponible: ¿reuso de recursos?
- Convivencia con otras redes en el mismo espectro / protocolo
- Sistema de captura asociado a  un proveedor



# Clase 2
12/03/26

## Arquitectura de IoT

Distintos participantes (*stackeholders*) tienen distintas visiones de la arquitectura de la IoT, donde existen proveedores como:

Existen proveedores de sistemas basados en Cloud Computing, proveedor de redes, sistemas de nodos/actuadores, entre otros. Generalmente son autónomos y que necesiten un humano al lado para funcionar (autónomo).

- Entes de *estandarización*
	*-> La idea es hablar el mismo idioma para comunicarnos*
	La idea es que la solución tenga mantenibilidad para el futuro.
	Debe cumplir, sino, no entro en la industria 
	SEC, seguridad eléctrica en Chile

- Consultoras
- Inversores en Tecnología
- Desarrolladores de Middleware y Sistemas Operativos
	La idea  es no preocuparse de problemas futuros, simplificando su instalación desde un inicio (mayor flexibilidad)

- Proveedores de soluciones basados en IoT

 - **Landscape 2018**
- Evolución de Gartner
	Gráfico de la expectación, caída y uso diario de tecnologías a través del tiempo

## Aplicaciones
Verticales de aplicación. Cuáles son las industrias que utilizan y a dónde encontraremos estos.

Agricultura, Salud, Industra, Seguridad, Home, Ambiente, Transporte, Militar, Instrumentación, Seguros (para saber a través de monitoreo si hay que aplicar algún seguro).

> Hay que entender el problema que estamos atacando para aplicar adecuadamente la solución.

### Transporte y Movilidad
- Monitoreo y Seguimiento de vehículos / flotas
- estado de vías ferreas
- Estructuras viales (puentes, túneles)
- Seguimiento de nivel de uso de transporte público
- Monitoreo de usuarios / fuerza de venta
- Trazabilidad

EJ) Tarjeta BIP
Es útil y cambia su valor interno rápidamente con los totems a una frecuencia de 5 MHz

QR: Quick response
# Clase 3
16/03/26
## Aplicaciones Pt. 2

### Entretención / Retail / Comercio

- Controles inalámbricos
- *Control de acceso*
- Monitoreo de fallas de juegos mecánicos
- Localización de usuarios
- Indicadores de precio
- Paneles de información
- Seguimiento de movimiento de usuarios

###  Industria

Monitoreo de:
- Refinerias 
- Vibraciones en túneles de minería
- Seguimiento en máquinas de minas a cielo abierto
- Fallas en rodillos de cintas transportadoras
- Smart Meters (Electricidad, agua, gas)
- Logística de basura
- Calidad eléctrica, consumos individuales de dispositivos
- Hoteles
	- Uso de recursos, detección de fallos
	- Iluminación de pasillos, logística de habitaciones

### Ambiente
Monitoreo de:
- Glaciares (movimiento, contaminación)
- Nivel de nieve para provisión de agua !!
- Flujo de agua en cuencas
- Avance de sedimentos y sólidos
- Sismos
- Incendios e inundaciones
- Desplazamientos de tierra y aludes
- Niveles de ríos y mareas

# Clase 4
19/03/26

## Aplicaciones Pt. 3

### Agricultura
Monitoreo de:
- Humedad y temperatura para el riego
- Niveles de fertilizantes
- Plagas
- Temperaturas en silos
	- Silo: Cilindros enormes contenedores de semillas
- Estado de animales (movilidad, temperatura)
- Seguridad perimetral
- Seguridad de alimento/liquidos
- Seguimiento en tambos (leche)
- Monitoreo de cámaras frigoríficas
- Seguimiento de cosechas manuales

### Salud
Monitoreo de:
- Parámetros en pacientes ambulatorios
- Seguimiento de equipos
- Localización de personal en hospitales
- Medición de calidad de medio ambiente
- Monitoreo de gases medicinales
- Control de acceso
- Trazabilidad de exámenes
- Paneles de información / turneros
- Seguimiento de acciones en hogares de tercera edad
- Seguridad en hogares de tercera edad
- Medición de performance en equipos de rehabilitación y entrenamiento

### Hogar / Oficinas
- Cámaras
- Control de acceso
- Control de aire acondicionado / iluminación
- Control de riego
- Botones para compra automática
- Monitoreo de consumo de servicios (gas, luz, electricidad)
- Monitoreo de mascotas (seguimiento, temperatura)
- Reporte de finalización de ciclos (edificios) (lavado, secado, microondas)
- Control de temperatura de agua para baño
- Reposición de insumos (máquinas de autoservicio, seguimiento de vencimientos, logística)


# Clase 5
23/03/26

Ej de espejo entrenador a traves de IA
# Clase 6
26/03/26

## Nodo - Hardware

Los nodos de forma estandar tienen estos componentes:
- Un mismo nodo puede tener multiples sensores
- Configuraciones dependen del fabricante y de la tecnología a usar

![[Pasted image 20260326102434.png]]

El controlador puede ser un *CISC* (x86) o *RISC* (arm)
Complex instructions set

- Un *DSP* para preprocesar info de señales de ancho de banda por ej
- Una *FPGA* para desarrollo
- Un *ASIC* para productos masivos y de alta performance

DSP -> más eficiente en sumas y productos
Muy eficiente para 1 tarea en especial
ASIC -> cuando no encuentro ni una wea para hacer

### Algunos ejemplos
- ATMEL AVR 
- ESP32 (pycom)
- ARM Cortex M3
- ATMEL ATMEGA
- Nordic 

### Radio
La radio tiene determinadas capacidades:
- Interfaz: Bit, byte, paquetes?
- Banda de frecuencias? 433MHz, 2.4GHz..
- Multiples canales?
- Velocidad de datos?
- Rango?

![[Pasted image 20260326111017.png]]


# Clase 7
09/04/26

## Nodo - Hardware

La radio tiene determinadas capacidades:

- Interfaz: Bit, Byte, Paquetes?
- Banda de frecuencias? -> 433MHz, 868Mhz, 915MHz, 2.4GHz
- Multiples canales
- Velocidades de datos
- Rango

Necesitamos mandar la menor cantidad posible de información
1. Por recursos
2. Cantidad de paquetes transmitidos al mismo tiempo en la red

![[Pasted image 20260409061717.png]]

- Escuchar es muy caro, por eso hay que ser eficiente
- El uso eficiente del espectro es importante
- Para asegurar que llegue bien el paquete tengo que protegerlo, trato de asegurar el envio de paquete en el espectro utilizado

En este caso, todos conviven en el mismo espectro con X cantidad de redes

- Tiene que ser tanto el uso del espectro como para interferir el envio de paquetes (aun no llegamos a ese punto)



-> Las telefonicas tienen uso de espectros fijas exclusivas para ellas
-> También para IoT

![[Pasted image 20260409063641.png]]

![[Pasted image 20260409063656.png]]


### Performance de la Radio

- Modulación
- Figura de Ruido
- Ganancia
- Sensibilidad
- Sensado de Portadora
- Rango de voltaje de alimentación


# Pre-Solemne 1
13/04/26

6 preguntas de desarrollo

1. Para un sistema de logística basado en gestión de flotas de vehículos, analice brevemente las sgtes caracteristicas

	Disponibilidad de Energía en el tiempo
	Patrón de funcionamiento
	Mantenimiento
	Escalabilidad:
	- Si yo puedo reproducir a un costo racional y poder manejar la capacidad para soportar la escalabilidad. 
	- ¿Hace falta mirar los 300 sensores al mismo tiempo en el mapa?
	- Puedo tener dispositivos híbridos

> Uno busca la aplicación primero para pasar a la tecnología a utilizar después

2. Considerando el mismo sistema de gestión de flotas de vehículos, diseñe una arquitectura adaptada a este problema y describa brevemente sus funciones

- Variedad de móviles a seguir ¿Qué tipo de flota?
	- Flota de camiones internacional, tren, autos
- ¿Cómo capturamos la info?
	Sensores como:
	- Ubicación: GNSS, GPS, Galileo
	- Captura de localización -> Wifi, bluetooth
- Capa de conectividad
- Servidores para bases de datos, procesamiento
- Visualización - Interfaz para cliente
- Posible incentivo

3. Describa 4 aplicaciones de la IoT en las siguientes áreas (una aplicación por área)

- Entretención
- Industria
- Salud
- Hogar

> Interfaz de usuario: Simbología fundamental para los seres humanos
	necesita un extra para medir algo o dar info de algo

Entretención: Controles de consolas, realidad virtual (audífonos no cuenta), Volantes de conducción

Industria: Sensor de gases (para botellas, si se puede usar o no)
Analizador de frecuencias, gases, que detecten

Salud: Refrigerador inteligente (con rfid), medidor de presión, medidor de sangre, timbres para avisar que están en habitaciones (múltiples puntos para sensorar), Detector de oxígeno

Hogar: Smarthome (sensor de movimiento, luces), aspiradora automática, aire acondicionado, detección de fuga de gas o agua

> Describir porqué es un IoT

4. ¿Cómo se logra reducir el consumo de comunicación en un nodo de IoT? Describa brevemente el método

- Mandando sólo lo necesario -> Compactar la información
- Enviar en un momento y dormir el resto del tiempo

4. ¿Cuál es la función del controlador en un dispositivo de IoT?

- Procesar
- Se monitorea a si mismo
- Actualiza la info de un lado a otro

6. ¿Por qué se usan múltiples canales para un ancho de banda ?

- Para evitar interferencia
- Para resilencia
- Para evitar saturación
- Canales pilotos para enviar mensajes para todos
- El resto del tiempo selecciono 1 canal para comunicarme con mis vecinos o con el destinatario especificado
- Diversidad de recurso para transmitir simultaneamente entre distintos IoT
- Los anchos de banda son muy pequeños por lo que no hace falta uno grande

EJ) Bluetooth en el metro, un canal en específico para no escuchar lo mismo que el resto de personas



---

# Clase 9
30/04/26

## Estructura de Dirección IPv6

Prefijo de red (64 bits) identificador de interfaz (64 bits) derivada del MAC (EUI-64)

Tipos de dirección 

### Ventajas de IPv6 sobre IPv4

Mayor tamaño de dirección y espacio de direcciones
Cuanto más eficiente es el metodo, más rápido 

Dirección global única por dispositivo + IPSec integrado + SLAAC = *despliegue masivo de dispositivos IoT sin configuración manual*.

SLAAC -> Configuración automática 


### Autoconfiguración en IPv6: SLAAC

Puede configurar su propia dirección sin servidor DHCP

1. Genra dirección link local (fe80::) a partir del MAC (EUI-64)
2. Escucha Router Advertisement *RA* del router
3. Extrae el prefijo de red del RA
4. Combina el prefijo + identificador de interfaz (64 bits del MAC)
5. Realiza *DAC* Duplicate Address Detection
6. Dirección global lista para usar

### Coexistencia  IPv4/IPv6: Dual Stack y Tunneling

La transición de IPv4 a IPv6 es gradual.

1. *Dual-Stack*: El dispositivo ejecuta [ambas pilas] simultáneamente. Usa IPv6 si el dispositivo lo soporta, IPv4 en caso contrario. El mecanismo más simple y preferido
2. *Tunneling*: Paquetes IPv6 [encapsulados dentro] de paquetes IPv4 para cruzar redes que solo entienden IPv4
3. *Translation* (NAT64): Traduce entre IPv4 e IPv6. Necesario cuando un host IPv6-only habla con uno IPv4-only

Los nuevos IoT vienen con *IPv6 integrado* de fábrica

### Reto: MTU

IPv6 requitere MTU $\geq$ 1280 bytes. 
IEEE 802.15.4 tiene MTU de solo 127 bytes

6LoWPAN resuelve esto con compresión y fragmentación de cabecera


### Encaminamiento: OSPF y OLSR

El encaminamiento determina el *camino óptimo* que siguen los paquetes de origen a destino a través de múltiples redes.

#### OSPF
- Protocolo de estado de enlace
- Cada router conoce la topología completa
- Algoritmo de Dijkstra para camino más corto
- Estándar en redes empresariales e Internet

#### OLSR
Versión optimizada para redes móviles ad-hoc (MANET). Precursor de RPL usado en IoT.

#### RPL: El Routing de IoT

Routing Protocol for Low Power and Lossy Networks
Es el protocolo de enrutamiento diseñado específicamente para IoT

### Fragmentación de Paquetes

La fragmentación divide paquetes grandes en fragmentos en el MTU del enlace subyacente. 

#### IPv4
- Cualquier router puede fragmentar
- Al destino final se reensambla
- *DF* Dont Fragment: Prohíbe fragmentación

#### IPv6
- Los routers *NO* fragmentan 
- el origen debe haber PMTUD
- Si paquetes muy grande -> ICMPv6 "Packet Too Big"
- MTU mínimo: 1280 bytes

### TTL: Time To Live
Previene que los paquetes circulen indefinidamente si hay bucles de enrutamiento

- IPv4: Campo TTL de 8 bits (0-255)
- IPv6: Campo Hop Limit (mismo concepto)
- Cada router decrementa el TTL en 1
- Si TTL = 0 -> Paquete descartado
- Se envía ICMPv4/ICMPv6 "Time Exceeded" al origen

*Traceroute*: Usa paquetes con TTL = 1, TTL = 2 para descubrir cada salto en el camino al destino. Mide latencia por salto y revela la topología.


# Clase 10
11/05/26

## TCP: Transmision Control Protocol

TCP crea circuitos virtuales entre gost y garantiza:

- *Fiabilidad*: Retransmision de paquetes perdidos
- *Orden*: reordenacion de segmentos desordenados (diversos caminos que puede tomar)
- *Control de flujo*: el receptor regula la velocidad
- *Control de congestión*: adaptación a la red
- *Multiplexación*: multiples conexiones por IP
- *Stream-oriented*: lectura como flujo de bytes continuo

> Si hay indice de perdida de paquetes, bajo mi flujo de transmision

Se pierden porque tenemos enlaces inalambricos (cosa que no existia en la creacion de TCP)

#### El precio de la fiabilidad
TCP es *heavyweight*: requiere 3 paquetes solo para establecer una conexión (3-way shandshake) antes de enviar cualquier dato util. (ponerse de acuerdo entre transmisor y receptor)

#### ¿Cuándo usarlo?
Cuando la perdida de datos es inaceptable
- Transferencia de archivos
- Navegacion web
- Correo electronico
- Bases remotas

No es el más eficiente para streaming, pero sigue siendo de los más usados

- No me interesa cuando hay paquetes repetidos o priorizo velocidad.
- No todos los protocolos son simétricos 


### Control de Flujo y Congestión

#### Control de flujo (Flow Control)
Previene que el emisor desborde al receptor
-> Nos permite ajustarnos al flujo que tenemos

- El receptor anuncia su window size disponible
- El emisor no puede enviar más que window size bytes sin ACK

#### Congestion Control
Previene el colapso de la red por sobrecarga

- Algoritmos: Slow Start, Congestion Avoidance, Fast Retransmit/Recovery
- Detecta congestion por perdida de paquetes o ECN
- reduce la ventana de congestión (cwnd) ante pérdidas


### Fiabilidad y Retransmisión en TCP
TCP garantiza entrega fiable mediante:

1. Numero de secuencia
2. ACK acumulativo
3. Retransmision por timeout
4. Fast Retransmit
5. Reordenacion

### *Problemas en redes IoT*
Las pérdidas son por ruido radio, no por congestión

- Latencia variable (puede ser enorme - latencia de 1 día)
- Alta tasa de pérdida (10-20%)
- Desconexiones frecuentes


## UDP

### Los 4 campos de UDP

1. Puerto Origen
2. Puerto Destino
3. Longitud
4. Checksum

### CoAP en UDP
CoAP http para IoT -> misma idea de url, puedo direccionar a un nodo determinado



# Clase 11
14/05/26


## AMQP: Advanced Message Queuing Protocol
Protocolo orientado a mensajes, estándar de OASIS -> Complemento asincrónico de HTTP

- NO es pub/sub  (intermedio) -> Especificacion de mensajeria interoperable
- Define un *wire format* -> reglas para selrializar bytes
- Cualquier cliente AMQP interopera con cualquier MOM que lo implemente
- Basado en un servidor de colas (*queue server*)

**Implementaciones populares**: RabbitMQ y Apache ActiveMQ

### Arquitectura 

- *Queue*: Almacén de mensajes 
	Persistentes (sobrevive desconexiones) o Dinámicas (creadas por consumidor)
- *Exchange*: Router de mensajes
- *Binding*: Enlace entre exchange y cola
- *Routing Key*: Etiqueta con sintaxis separada por puntos
	Soporta wildcards (\*, #)

> AMQP Es más flexible pero más verboso que MQTT.

Menos adecuado para dispositivos muy restringidos, pero excelente para brokers en el backend.

### Casos de Uso

1. Message Queue: 
2. Fanout: Publicar a multiples consumidores simultaneamente
3. Routing: Despacho inteligente por routing key
4. RPC (Remote Procedure Call): Solicitud-respuesta asincrona
5. Work Queues: Distribucion de tareas entre workers



## SIP: Session Initiation Protocol
Protocolo estándar IETF de capa de aplicación para *establecer, modificar y terminar sesiones*.

- protocolo de texto, similar a HTTP
- Modelo cliente/servidor
- Métodos típicos: REGISTER, INVITE, BYE, ACK
- Transporte: *UDP* por defecto, tambíen TCP, TLS, DTLS
- Negocia parámetros de sesión con SDP

### Casos de uso
- BoIP (llamadas de voz sobre IP)
- Videoconferencia
- Mensajería instantanea
- IoT con sesiones (streaming de datos)



### Arquitectura SIP

- *User Agent (UA)*
	Terminal SIP. Puede ser cliente o servidor
- *Registrar Server*
	Recibe registros SIP. Mantiene  el binding SIP AOR -> dirección de contacto
- *Proxy Server*
	Intermediario que reenvía solicitudes en nombre de otros clientes
- *Redirect Server*
	Redirige al cliente hacia otro servidor
- *SIP AOR*
	Addres of Record, similar a un email






## SDP: Session Description Protocol
Describe los parámetros de la sesión a establecer. Se transporta como payload de los mensajes SIP

En escenarios IoT, SDP puede negociar:
- Puerto UDP para los datos del sensor
- Formato de datos (JSON, CBOR)
- Frecuencia de muestreo
- Protocolo de transporte (UDP, CoAP)

Esto es lo que CoSIP adapta para entornos restringidos


#### Limitantes
Los mensajes SIP/SDP son texto verbose, 500 bytes frente a 127 bytes soportables de IoT

- Mensajes grandes (+500 bytes)
- Alto costo de parsing
- Mayor footprint de RAM

> Inapropiado para dispositivos restringidos




# Clase 12
28/05/26

Sistemas operativos 
- Estándar
- Scheduler
- *En tiempo real*



# Clase 13
01/06/26

## IIoT - Internet Industrial

Es IoT *aplicado a industrias*: manufacturas, logistica, petroleo y gas, transporte, energía, mineria, aviacion.


#### Diferencias
1. Tiempo real
	El IoT de consumo = pocos segundos
	IIoT real = submilisegundos
2. Fiabilidad extrema
	Un fallo en la red eléctrica, control aereo o una fabrica tiene consecuencias graves. *Best-effort* NO es aceptable
3. Vida util larga
	Los equipos industriales se usan 15-30 años. Los protocolos deben soportar legado.

PLC: Controlador Logico Programable

#### Consecuencias de fallos en IIoT
El IIoT requiere niveles de fiabilidad, seguridad y determinismo radicalmente superiores al IoT de consumo

- Una red eléctrica: millones de afectados
- Control de tráfico aéreo: riesgo de vidas
- Fábrica  automatizada: pérdidas millonarias
- Planta química: riesgo ambiental y humano


### Protocolos

1. Modbus (1979 - Modicon)
	- Protocolo maestro/esclavo para comunicación con PLCs
	- Simple, robusto, ampliamente desplegado
	- Versiones:
		- Modbus RTU (series) (Remote Transmition unit)
		- Modbus TCP (Ethernet)

2. OPC-UA (OPC Foundation, 2006)
	- Open Platform Communications
	- Framework de interoperabilidad industrial con modelo de información y seguridad integrada
	- Agnóstico al transporte: TCP, HTTPS, MQTT, CoAP
	- Escalable: desde sensor hasta nube empresarial
	- Soporte de semántica: tipos de datos, metodos, eventos

#### Otros protocolos industriales clave

1. HART
2. PROFIBUS
3. PROFINET
4. EtherNet / IP


### IT vs OT

#### IT - Information Technology
Sistemas de información corporativa

#### OT - Operational Technology
Sistemas de control industrial


- 802.15.4
 Todos comparten este canal

### Requisitos de teimpo real en el IIoT

| Aplicación            | Latencia (ms) | Tecnología    |
| --------------------- | ------------- | ------------- |
| Control de movimiento | < 1           | EtherCAT, TSN |
| Controd de proceso    | 1-10          | PROFINET      |
| Supervision SCADA     | 10-100        | WirelessHART  |
| Monitoreo condicion   | 100 - 1s      | IEEE 802.15.4 |
| Telemetria datos      | 1-60s         | CoAP, MQTT    |
| Gestion activos       | Minutos       | HTTP, REST    |

### El Problema de ciberseguridad en IIoT

- Los sistemas OT fueron diseñados para redes *aisladas fisicamente*. Sin cifrado ni autenticacion, sin actualizaciones
- La convergencia IT/OT conecta estos sistemas a redes IP y eventualmente a internet
- *Disponibilidad* es prioridad en OT (vs confidencialidad en IT)




# LAB 1
04/06/26

## Intro

Configurar una radio IEEE.802.15.4: 
- Enviar y conseguir tramas unicast y broadcast
- Demostrar el aislamiento por canal

Inicializar RPL (enrutamiento)
- Configurar nodo raiz
- verificar formacion del DODAG
- Interpretar tabla de enrutamiento

Lo que debe cambiar es el Canal y PAN_ID por grupo para no colisionar paquetes



# Clase 15
08/06/26

## Interoperabilidad en IoT

### ¿Por qué es el desafío central de IoT?

El IoT conecta dispositivos de fabricantes distintos, con protocolos distintos y datos en formatos distintos.

- Sin interoperabilidad cada fabricante construye su *silo propio*. Sus dispositivos solo hablan con su nube, su app y sus servidores.
- Esto impode la visión real de IoT: un ecosistema donde cualquier dispositivo interactúa con cualquier otro.

**Consecuencias**
- El usuario necesita una app por fabricante
- Los datos no fluyen entre plataformas 
- La integración entre sistemas es costosa y frágil

> La interoperabilidad es el problema NO resuelto del IoT

### Origen del Problema: Arquitectura Vertical

Los primeros días del IoT usaron el enfoque más simple: dispositivos directamente a la nube del fabricante.

1. Smart objects envian datos por MQTT/HTTP sobre TLS
2. La plataforma cloud almacena los datos
3. Una app del fabricante accede via HTTP

**Problema:**
- *Silos verticales*, la plataforma controla completamente los datos y las APIs
- Los dispositivos están diseñados para hablar *solo* con esa plataforma específica

#### Los 5 Problemas de las Soluciones Verticales

1. Escalabilidad
2. Disponibilidad
3. Interoperabilidad
4. Seguridad
5. Evolución

## Modelos de Comunicación

1. Request / Response
	Cliente inicia, Servidor responde.
2. Publish / Subscribe
	



