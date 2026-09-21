
# Clase 2
13/08/26

## ThinkDSP



# Clase 4
20/08/26

## Capítulo 2: Harmónicos

Una señal en la realidad parte de 0. Para reproducir seria reducir la amplitud a 0 y quizas normalizar la señal.

Framerate = cantidad de muestras

### Espectros de señales cuadradas
Tienen solamente comppnentes impares, porque o si no explotan

Si yo tengo una señal a 5000 Hz, no lo puedo muestrear a mas de 10.000 muestras porque empieza a tener *aliasing*

*Aliasing* -> Efecto de distorsion que ocurre cuando una señal continua se convierte en datos digitales usando una frecuencia de muestreo muy baja.

Muestreo mas lentamente de lo que esta pasando realmente

EJ)

![[Pasted image 20260820110727.png]]

Los mojoncitos son reflejo de la misma señal pero reflejado a la izquierda dado que no hay mas espacio para mostrar informacion.

# Clase 5
24/08/26

Si la señal cuyo promedio no sea 0, la frecuencia tiene un valor constante *NO existe*.
Frecuencia 0 gasta energía.
*Ventaja* -> Para alimentar un circuito que ademas amplifica una señal.

**Acople** -> En sonido se retroalimenta, tiene una exponencial creciente
	Se puede convertir una frecuencia en tiempo real a frecuencia, generando un nuevo espectro donde no haya acople

n = Numero de muestro
d = Tiempo entre saltos

-> Hace falta la amplitud y la fase para construir una señal


# Clase 6
27/08/26

Hay que saber interpretar qué es lo que representa una señal, por ejemplo una frecuencia periódica de un puente representa qué tanto oscila por el viento
## Señales NO Periódicas


Lo que hacemos es sencllamente ajustarla aplicando una ventana (aunque quede feo) para 
que no aparezca energia en frecuencias donde no la hay. Se reduce (no llega a 0) pero es mucho mejor que tenga energía que no existe.

![[Pasted image 20260827103749.png]]

De esto a:
![[Captura de pantalla_20260827_103756.png]]



### Espectograma

![[Pasted image 20260827103857.png]]

Es la representación real de una transición. 
	Un espectograma es una visualización de un corto periodo DFT que permite ver cómo el espectro varía sobre el tiempo


Si le agregamos una 3ra dimensión llamada *tiempo* -> Frecuencia, tiempo y amplitud

Tiempo, frecuencia y el color amarillo es la amplitud

![[Pasted image 20260827104629.png]]


```
signal = Chirp(start=220, end=440)
wave = signal.make_wave(duration=1, framerate=11025)
plot_spectrogram(wave, 512)

Time resolution (s) 0.046439909297052155
Frequency resolution (Hz) 21.533203125
```

Mientras más grueso el valor verticalmente, mejor resolución temporal el que tengo


!!!! Hacer ejercicios de reicevebook o similar para testear señales

# Clase 6: PPT

### Hadoop

Resumen
- Yarn consiste en una mejora basado en hadoop
- *Problema*: Localidad y tiempo de ejecución
	- Un mismo bloque de info se está consumiendo de distintas queries
- Funciona a traves de scheduler para tareas locales
- Relevancia:
	- Trafico de red -> Latencia reducida 
	- YARN actualmente es el principal manejador de recursos para empresas como facebook, yahoo o linkedin.
- Resultados
	- Trade-off entre localidad y tiempo de respuesta, se incrementa la localidad

Preguntas
- ¿Por qué se usa una versión específica de hadoop, en este caso 2.3.0?
	R: La versión más estable a la hora de resolver la problemática
- Si aumenta el tiempo de respuesta, ¿En que me beneficia si mejora la localidad?
	R: Depende del caso, no existe un óptimo global

Nota sugerida
7



# Repaso Solemne 1
07/09/26

Procesamiento Digital de Señales 2020

**Desarrollo**

Utilizando las librerías thinkdsp y numpy de Python, en el entorno Notebook resuelva:

1. La señal “cuadrada.wav”, que contiene una señal cuadrada, fue muestreada a 11025 muestras/s. Establezca la frecuencia fundamental de la señal, considerando que es posible que la velocidad de muestreo genere aliasing. Reconstruya la señal filtrando las componentes - si es posible - para que no ocurra aliasing, en ese caso.
    
2. La señal “desconocida.wav” contiene una señal desconocida. A partir de análisis temporales y de espectrograma, describa el tipo de señal encontrada (forma de onda, variación con el tiempo, etc.)
    
3. La señal “incognita.wav” contiene una señal recibida desde el espacio exterior. Se sospecha que es una señal muy débil cubierta de ruido, y que la señal solo puede ser triangular de 1000Hz o 2000Hz, diente de sierra de 1500Hz o cosenoidal de 500Hz. ¿Es cierto? Si lo es, ¿qué señal está enmascarada?
    

# **Informe**

Redacte un informe en Python Notebook que contenga:

1. Título
    
2. Descripción del proceso realizado
    
3. Los códigos utilizados
    
4. Gráficos que ilustren los resultados
    
5. Análisis de resultados que respondan a las tres tareas enumeradas 

# **Pauta de Corrección**

Para la corrección de esta Evaluación se tomará en cuenta:

Condición necesaria pero no suficiente de aprobación: El código debe funcionar de manera comprobada.

Presentación: Todas las secciones mencionadas deben existir en el informe

Debe respetarse el formato solicitado.

Calidad del análisis de los resultados: El texto debe contener de manera clara y precisa la explicación de por qué se observan esos resultados.

Claridad y especificidad en la explicación del código en la introducción y su coherencia con los resultados mostrados.

La conclusión debe resumir los puntos importantes del informe.


---

# Capítulo 5
21/09/26

¿Cuánto se parece una señal a si mismo? Encontrar una señal dentro de otra

Para investigar la correlación de una señal, comenzamos con una señal seno

La autopoblación sirve para saber qué tan correlacionadas están las señales.
¿En qué momento partió la señal y cómo puedo sincronizarme con esta?

Cuando el valor de correlación es igual a 1, es cuando la señal es exactamente la misma que la 2da

![[Pasted image 20260921102847.png]]


Cuando el valor de correlación es -1,  la señal se cancela dado que es su opuesta

![[Pasted image 20260921103511.png]]

Si la señal es un coseno y graficamos el valor de la correlación, generamos un coseno

![[Pasted image 20260921103851.png]]

Hagamos correlación pero con ruido 

Generador de pseudo espectro. 
- Me sirve para sincronizar mi señal con el que quiero transmitir, si es similar al ruido, 
- Generando una señal con mucho ancho de banda, con pseudo-ruido (se repite con un periodo muy largo), para los demás parecerá ruido, pero yo como receptor la correlaciono con el mismo codigo que el transmisor y asi puedo codificar la señal de manera "oculta".







