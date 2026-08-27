
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
