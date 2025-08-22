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

