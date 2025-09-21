# Clase 2
08/08/25
## Conceptos básicos

- Medio Físico
	Medio de transporte para la información (señales eléctricas) de forma cableada o inalámbricamente
	
-  Medio Confinado
	(Cable) Vía de transporte donde se propaga información sin salirse de este medio. 
	Evitar la inducción electromagnética
	 
- Espectro
	Segmento de la atmósfera por el que viajan las ondas de energía.
	Rango de frecuencias propagadas a través de un medio físico, siendo un bien nacional de uso público.
	Administrado por SUBTEL, dividido en rangos de frecuencias ISM
	
- Multiplexión
	Capacidad de separar múltiples señales a través de un enlace de comunicaciones común
	Técnica donde transmito flujos de información a través de un medio físico: de un cable 
	- Espacial: Distribución por diferentes espacios ej. Multiples antenas, cables (MIMO)
	- Temporal: Info distribuidas en ranuras (slots) alternas de tiempo
	- Frecuencia: Info distribuida en frecuencias a través del espectro.

- dB
	Intensidad sonora. Unidad logarítmica que relaciona potencias (output con input).
	Por si sola **NO es una unidad de medida**. Cuántas veces se amplificó cierta salida
	$$10\space log_{10}(\frac{Output} {Input}) \space = \space dB$$
	
- dBm
	Relación de potencia con miliwatt. ==Expresión de potencia==.
	Potencia relativa respecto a 1mW.
$$ 10 \space log_{10}(1) \space = \space 0 dBm$$

- Relación Señal a Ruido (SNR)
	Diferencia entre la potencia de señal de información y de ruido
	- *Ruido:* Mínimo nivel de recepción de señal. No se puede interpretar nada.
	La señal tiene que ser mayor al nivel de ruido
	Que yo tenga más barras de wifi significa nivel de señal. Menor barritas, mayor ruido que tengo y poca señal.
	
- Relación Señal a Interferencia (SNIR)
	- Interferencia: Otra señal operando en la misma señal (Frecuencia) en la que estoy

- Ancho de Banda
	Rango de frecuencias donde se está transmitiendo.
	Velocidad de transmisión Mbps, etc.

- Eficiencia Espectral
	Medida teórica de cuánta información (X bps / Hz) puedo transmitir en 1Hz de espectro.
$$n = log_2(1 + SNR)$$
- Capacidad
	Máxima eficiencia espectral. (casi nunca se llega)

# Clase 3
12/08/25

## Conceptos básicos P2


- Modulación
	Alterar una señal auxiliar en función de una señal de información.
	Modifico sus parámetros (funcion auxiliar)

- Modulación AM/FM/PM
	AM: Amplitud
	FM: Frecuencia
	PM: Fase (Phase) *Modulación Compleja*

- Modulación Compleja
	Mapeo de información en simbolos, a mayor SNR, más complejas pueden ser las modulaciones a usar. %%Cuadrante que representa los bits que envio por simbolo.%%
	
	BPSK
	QPSK
	QAM
	8QAM
	16QAM, etc

	Cantidad de bits que quiero modular.
	Modulaciones adaptativas en función a la SNR. Más bajo la modulación, más bajo el SNR

- Baudios
	Cantidad de Símbolos por segundo a transmitir

- Ecualización
	Amplifica o disminuye sonidos.
	Modifica la intensidad o amplitud dentro del rango de frecuencia 
	Ajuste dentro de determinados valores las frecuencias de reproducción de una señal.

### Términos de Red

- Paquete
	Conjunto de información que enviaré desde A hasta B.

- Trama
	Conjunto de paquetes enviados a un medio

- Tipos de mensajes (cast)
	Broadcast, multicast, unicast

- Estrategias de Duplexión
	Full duplex: En ambas vías simultáneamente (discord)
	Half duplex: En ambas vías intercalado (O escucho o hablo)
	Simplex: Una sola vía (Un solo sentido)

- Mecanismos de Acceso al Medio
	Organización / Estrategia de cómo yo organizo a los usuarios dentro del sistema
	- En Tiempo
	- En Frecuencia
	- En Código (llave única)

- Mecanismos de Acceso al Medio Con y sin Contienda
	En x segundos transmito por el medio: 
	- Con Contienda: Luchando por comunicarse, Me peleo el medio por el que transmito
		Mayor probabilidad de colisión. En caso de suceder retransmite
	- Sin Contienda: Organizo para que se pierda la menor cantidad de info posible

- Mecanismos de ARQ (Automatic Repeat-reQuest)
	Mecanismo de Retransmisión
	Mensaje enviado automaticamente al momento de fallo o recibo correcto.

- Calidad de Servicio
	Satisfacción del cliente 
	- Cobertura
	- Tiempo de demora
	- Estabilidad

# Clase 4
19/08/25

Propiedades de dB, dBm y logarítmicas.

0 dB + 0 dB = 0 dB?

$$ 10^{0/10} = 1 vez ganancia $$
$$10 \space log_{10} \cdot (PO'' / Pi) = 0 \space dB$$

dado que PO' = Pi, PO'' = Pi


- Propiedades logaritmicas:
$$ A \cdot log_B(C)^D = E $$
$$A \cdot D log_B(C) = E \space => \space B^{E/(A \cdot D)} = C$$


10 dBm + 0 dB = 10 dBm? CORRECTO

10 dBm + 10 dBm = 20 dBm?
NO, para la suma debo pasarlo a suma lineal

10 mW + 10 mW = 20mW
$$10log_{10} (20mW/1mW) = 13 \space dBm$$

**dBW**
$$10log_{10}(P / 1W)$$
$$10log_{10}(10mW / 1000mW)$$


1 Watt = $10log_{10}(1 * 1000mW/ 1000mW)$

- 0 dBw + 0 dBm = ?

0 dBw = $10^{0/10} = 1W$, luego 1W + 1mW = 1001 mW

$dBm \space = \space 10log_{10}(1001mW / 1mW) = 30.0043 \space dBm \space = 30 dBm$

si escribo 4.340 x 10 ^-3 dBw MALO, debiera decir 0 dBw

- 3 dB (multiplicador x2)

$10^{3/10} = 1.99526 = 2 \space veces$ 

# Clase 5
22/02/25

## Espectro Radioeléctrico

Porción del espectro usado para telecomunicaciones, encontrado antes que el infrarrojo
Infrarrojo -- Control remoto
	Diodo en el extremo, donde a través de este transmite la onda infrarroja
	
![[Pasted image 20250822160908.png]]


*Multi-trayectoria*: La señal rebota a cierto objeto para llegar al destino deseado, depende de la distancia.

*Pathloss* Cuanto estoy perdiendo energía en función de la longitud de distancia.
Menor longitud de onda - Mayor obstaculidad de transmisión de onda

- Es infinito
- A mayor frecuencia, más perdidas
- A mayor frecuencia, menor tamaño de antena
- A mayor frecuencia, mayor necesidad de linea de vista

$$ \lambda = C/f$$
$\lambda$ = Longitud de onda
C = Velocidad de la luz = $3 \cdot 10^8$ m/s 
$f$ = Frecuencia



| Frecuencias |             | Uso                                              |
| ----------- | ----------- | ------------------------------------------------ |
| 3kHz        | VLF         | Comunicaciones de banda estrecha (mas de 1000km) |
| 30kHz       | LF          | Larga distancia, sobre el horizonte              |
| 300kHz      | MF          | Radiodifusión AM com. marítimas                  |
| 3MHz        | HF          | Radiodifusion internacional                      |
| 30MHz       | VHF         | Radiodifusión en FM, Radios móviles, aeronáutica |
| 300MHz      | UHF         | Transmisión en TV, celurales, WLAN               |
| 3GHz        | Micro-Ondas | Enlaces punto a punto, satelites, FWA, WLAN      |
| 30-300HGz   | MM-ondas    | Servicio de ondas milimétricas                   |
![[Pasted image 20250822164726.png]]

- Por qué las transmisiones AM tienen más alcance que las WLAN?
Estas ondas pueden rebotar en la ionosfera y regresar al suelo


Uso del Espectro
- Insumo esencial, finito, de complicada administración.
- Su uso se comparte ente empresas de broadcasting
- Clima: las gotas de agua de lluvia pueden obstruir la transmisión de señales. No afecta a señales de frecuencias bajas, sí a ondas cerca de 30-300GHz

### Evolución Telefonía Celular

En los comienzos de la década del 2000, el número de conexiones inalámbricas supera a las fijas.

- ¿Cuál es el cuello de botella para aumentar la capacidad de red? 
	1. Ancho de banda
	2. Latencia y retraso de propagación
	3. Capacidad de routers, switches, etc
	4. Interferencias y congestión del canal
	5. Capacidad del enlace de última milla
		- Ley de Moore sobre el problema de acceso de última milla
		Ultimo tramo de una conexión, desde el proovedor de servicios de internet (ISP) hasta el usuario final.




# Clase 6
29/08/25

**Embotellamiento de Botella**
distribución de un sistema ofrecido a los usuarios de un servicio.

## Principales usos del Espectro

A frecuencias más altas, menor cobertura
Longitud de onda:
$$ \lambda = \frac{C}{f} : Donde \space C \space = \space 3\cdot 10^8 $$
### Evolución a la Telefonía Celular

1. 1ra generación
	Tecnología análoga
2. 2da generación:Tecnología digital
	- GSM
	- CDMA: Multiples usuarios en la misma frecuencia
	- TDMA: 
2da generación + multimedia
	Email, Internet, Mediciones, Localización, Seguridad

3. 3ra generación: Tecnología digital

###### 1ra generación
En un inicio era sólo transmisión de voz. No habia seguridad en transmitir y comunicarse además de la baja calidad.

###### 2da generación 
Sienta las bases de los estandares masificado en GSM.Se complejiza más en relacion a las modulaciones complejas. Aparece CDMA y TDMA

###### 2.5da generación 
- Mejora en comunicación de usuarios. Envío de mensajes por texto, no solo por texto
- GPRS: Cambio de modulación.
- Voz: la comunicacion empieza a ser más entendible.
- Conexión a internet en pañales
- Email, Internet, Mediciones, Localización, Seguridad

###### 3ra generación
Estándares a nivel global, concretados por grandes empresas (3GPT): empresa dedicada a la estandarización. 2Mbit por segundo como máximo de velocidad de datos.
- Servicios basado en imágenes

Mientras más avanzan las generaciones, se reducen los costos de producción y de venta de las tecnologías.

##### AMBS 
1er standar desarrollado para tecnología celular
- Desarrollado por "Bell Laboratories" en 1970, Estados Unidos.
- Uso comercial en 1983.
- Patrón de reutilización de 7 celdas
- *Celda:* espacio donde abarco cierta cobertura para dar comunicación a los usuarios
- Esta admite sectorización y división de celdas

A las empresas se les asigna una porción de espectro para su uso de comunicación a los usuarios.
Al ser tan grande, se debe reutilizar la frecuencia usando las celdas. Se puede lograr con clusters de celdas, distribuyendo la frecuencia completa dentro de cada celda.

Por cada celda, se usa x canales de comunicación.
Si uso el mismo canal en otra celda, habrá intermitencia.
Cada canal tiene 1MHz, teniendo por ej 100 canales en total.

*Cluster*: Conjunto de celdas (normalmente 7 celdas por cluster)
Se reutiliza la frecuencia entre clusters

*Enlace BackHole* Conexión por fibra óptica que conecta clusters en Chile

- Mientras que el 3G demoró 12 años en alcanzar mil millones de usuarios, 5G supero la misma cifra en 3 años y medio, alcanzando los 2400 millones a marzo de 2025
- 121 paises alrededor del mundo que cuenta con 5G


# Clase 7
02/09/25


## LANs Inalámbricas

- Nivel fisico
- MAC
- Ej de aplicaciones
- Puentes inalámbricos
##### Comparación Tecnologías Inalámbricas móviles

| Tipo de Red          | WWAN (Wireless WAN)                     | WLAN (Wireless LAN)       | WPAN (Wireless Personal Area Network) |
| -------------------- | --------------------------------------- | ------------------------- | ------------------------------------- |
| Estandar             | 5G                                      | IEEE 802.11 Wi-Fi         | IEEE 802.15 Bluetooth                 |
| Velocidad            | LTE: de 1kb/s hasta 1Gbps - 5G: 10 Gbps | hasta 40 Gb/s             | 2Mb/s  < 100Mb/s                      |
| Frecuencia           | 700 MHz - 6GHz                          | Infrarrojos, 2.4GHz, 5GHz | 2,4 GHz                               |
| Rango                | 35Km                                    | 30-300m                   | 1-100m                                |
| Técnica Radio        |                                         |                           |                                       |
| Itnerancia (roaming) |                                         |                           |                                       |

#### Link Budget
Nivelación de enlace *de forma lineal*

$\lambda$ = Longitud de onda = $C / f$
$P_R$ = Potencia receptor
$P_T$ = Potencia transmisor
$G_T$ =ganancia equipo transmisor
$G_R$ = Ganancia equipo receptor
$d$ = Distancia
$n$= Exponente de Pérdida
$$ P_R = P_T \cdot G_T \cdot G_R \cdot ( \frac{\lambda}  {4\pi d})^n$$

Cuando $n$ es igual a 2 --> Modelo Friis *Máxima pérdida*

Frecuencias mas bajas, mayor longitud de frecuencia, mayor tamaño de antena

$P_R$ tiende a perder por $1/d^2$
$P_R$ tiende a perder por $1/f^2$


### Alcance de las ondas de radio en función de la Frecuencia

![[Pasted image 20250902164747.png]]


### Nivel físico en 802.11

- Infrarojos
	Sólo válidos en distancias muy cortas (10-20m) y en la misma habitación.

- Radio
	- FHSS Frecuency Hoping SpreadSpectrum
		Sistema de bajo rendimiento, poco usado actualmente
	- DSSS
		Buen rendimiento y alcance. Sentó las bases para su digievolución en 802.11b (hasta 11Mb/s, 2.4GHz).
	- OFDM
		Original ente empleado en banda de 5GHz (menor alcance que 2,4GHz)
		Divide en multiples subcanales (hasta 256 subportadoras), donde cada una de ellas puede ser modulada en relacion SNR mejorando la eficiencia espectral.

Mayor SNR -> 16 BPM
Menor SNR -> BPSK

# Clase 8
05/09/25

Recordar:
$$P_R = P_T \cdot G_T \cdot G_R \cdot (\frac{\lambda}{4\pi d})^n$$ 
### Regulación del Espectro e Importancia de las bandas ISM

ITU-R Regula la mayor parte del espectro: Se necesita licencia para transmitir

- Divide el mundo en 3 regiones, cada una con reglas distintas. Algunos países tienen sus propias reglas
- IEEE definio el uso de bandas ISM (Industrial Scientific Medical) para Wi-Fi y otras tecnologías sin licencia
- Las ISM no son idénticas en todo el mundo: varían según país y región


![[Pasted image 20250905163855.png]]


En la banda de 2,4GHz, toda transmisión con potencias superiores a 1 mW debe emplear técnicas de espectro ensanchado para reducir interferencias

Existen 2 métodos principales:
- *Frequency Hoping (salto de frecuencia)*
	El emisor va cambiando continuamente de canal. El receptor lo sigue (Bluetooth clásico)
- *Direct Sequence*
	Usa la comvolucion con llave unica para cifrar la conexión. Usa un canal de ancho mayor y convoluciona la señal con un tren de pulsos estrechos asignada a cada usuario.


![[Pasted image 20250905163909.png]]

- Frequency Hopping
	Para combatir la interferencia, cambia a un canal que no tenga

- Direct Sequence
	Cada comunicación se encuentra cifrada, además el canal es muy ancho, transmitiendo mucha información redundante.

![[Pasted image 20250905164138.png]]



![[Pasted image 20250905164310.png]]



#### Canales de Wi-FI en la banda de 2.4GHz

![[Pasted image 20250905165001.png]]

se intercalan los canales cada 5MHz de forma nacional e internacional alrededor de los 2.4GHz

#### Canales DSSS Simultáneos

Si se quiere usar más de un canal en una misma zona, hay que elegir frecuencias que no se solapen. El máximo es de 3 canales.
	- EEUU y Canadá: Canales 1, 6 y 11
	- Europa: Canales 1, 7 y 13

- Con diferentes canales se pueden construir LANs inalámbricas ==idependientes== en una misma zona

#### Banda de 5GHz (802.11a)

IEEE definió en 1999 el estándar 802.11a en la banda de 5GHzm aprobado por la FCC de EEUU, permitiendo usar canales de mayor ancho de banda y con OFDM de hasta 54Mb/s.

- No muy popular al inicio porque los equipos eran caros y el rango en 5GHz era más limitado.
- 802.11n unificó en 2009 2,4 y 5GHz

- Un equipo 802.11a NO puede interoperar directamente con uno 802.11b


### Interferencia debida la Multitrayectoria

Ocurre cuando una señal llega al receptor tanto de forma directa como reflejada en paredes, techos u objetos. La señal reflejada recorre un camino más largo y llega con retraso.

![[Pasted image 20250905171007.png]]

### Diversidad de Antenas
Multiplexion espacial

El equipo dispone de 2 o más antenas que reciben de manera independiente
- En cada trama se evalúa cuál antena entrega mejor señal, y se utilizada para la recepción
- NO sirven para ampliar cobertura, sino para mejorar la calidad de señal