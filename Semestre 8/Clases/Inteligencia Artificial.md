johan.fuentes@mail.udp.cl
# Clase 1
05/08/25

Siempre partir buscando la solución más simple posible

*Inteligencia Artificial*
Sistema se comporte como humano o mejor: Razonar, aprender, percibir su entorno, aprender y actuar de forma inteligente para alcanzar objetivos. Existen 4 enfoques.

##### Actuar como Humano
Lo observable se parezca un humano (ChatGPT), pero no por eso por dentro haga procesos igual que uno (Test de Turing).

##### Pensar como Humano
Modelos cognitivos en ACT-R
Se enfoca en modelar el pensamiento humano, que piense como lo haria una persona

##### Pensar Racionalmente
Sistema Experto
Intenta reproducir el pensamiento lógico correcto, visión idealizada de como deberia pensar

##### Actuar Racionalmente
Vehículo autónomo (más usado actualmente)
- Objetivos definidos
- Percibe su entorno
- Toma decisiones para maximizar el éxito
- Adaptable a nuevos escenarios

### Clasificación de Tipos de IA

- Reactivas / Basadas en reflejos 
	Ajedrez
- Basada en Estados
	Control de personajes de un juego
- Basada en Variables
	Predicción del precio de una casa o de las acciones de la bolsa


Transformers -> Cosas agregadas a la red neuronal (EJ Chatgpt)

- Modelos bayesianos
- Algoritmos de clustering
- Algoritmos de regresión y clasificación
- Redes neuronales
  Metaheurísticas

Repasar Calculo 3, Probabilidad y estadísticas. 
Google colab (ejecutar pyhton por separado)


# Clase 2
08/08/25

Propiedades de Probabilidad
###### Teorema de Bayes
Que tan probable que Y resultado haya sido causado por Xi causa
Y Resfrio
Xi,Xj,Xk = Causas ( T, I, R)

## Red Bayesiana

Modelo probabilístico que representa grafos acíclicos dirigidos.
Cada nodo representa una variable. La flecha una condicionalidad.

Lluvia ----------> Piso mojado --> Tráfico lento
Aspersor -------> 
Caida de vaso ->

*Polytree* Un solo camino viable que pueda conectarme hacia cierta variable.
Se puede calcular en tiempo lineal SOLO si es *polytree*, puede tener múltiples padres.

Se representa mejor en la realidad como grafo acíclico dirigido.

### ¿Para qué sirve?

Para Inferir que causa es más probable que haya sido responsable del resultado.

Predicción: De arriba hacia abajo
Inferencia: De abajo hacia arriba

- P(A), P(B) 
- P(C): Probabilidad total 
(si ocurre A dsp de B) (si ocurre sólo A) (si ocurre sólo B) (si ocurre ninguna)
- P(D|E): lo mismo que C
### Dependencia de Sucesos

B -> C -> E

Si yo no conozco C, pero sí E
Para calcular P(B | E), ¿puedo descartar C? NO 
vendría siendo P(B | C , E)


EJ) A=lluvia, C=suelo mojado, E= tráfico

A = 
C = *Independencia Condicional*
E = 

*Serie*                     A -> C -> E
*Convergente*        A -> C <- B
*Divergente*           D <- C -> E

EJ) 
![[{7322476E-69FF-44CF-A08E-54A64C94886D}.png]]


# Clase 3
12/08/25


## Cadenas de Markov

- Proceso estocástico de memoria corta
- Describe una secuencia de eventos
- Ahora los nodos presentan *estados* en el tiempo y las *aristas* representan *transiciones temporales*

###### Definiciones
- Estocástico: Transita a otro estado con cierta probabilidad
- Determinista: Transita a otro estado siempre
- Memoria corta: Su probabilidad de estar en un estado sólo depende de la probabilidad/estado anterior

Pasar de un estado a otro desde un punto suma 100%

Probabilidad del siguiente estado Markov Orden 1:
$$P(X_t \space|\space X_{0:t-1}) \space = P(X_t \space | \space X_{t-1})$$

### Matriz de Transición

Las probabilidades de un estado a otro se representan con una matriz

Mostrar foto de matriz**

### Vector π - Distribución estacionaria

Representa la probabilidad a largo plazo de estar en un estado

Si hay 3 valores que puede tomar la variable, π puede tener 3 valores.

π = [P, B, H]
π = [0,2 0,9 0,1]

**Estacionaridad:** π = πA

Hay 3 formas de calcular π

Sistema lineal
- Resolver π = πA
- Restricción = $\sum _I \pi_I = 1$ 

A= 

| 0   | 0,3 | 0,7 |
| --- | --- | --- |
| 0,6 | 0,2 | 0,2 |
| 0   | 0,5 | 0,5 |

$U_1$ = [0, 1, 0]

Para que \pi converja

- Un estado pueda llegar a todos los estados
- Numero de markov tenga limitado los 

## Modelos ocultos de Markov (HMMs)

En este modelo no conocemos la secuencia. Lo único que se es el resultado de la elección. A través de esto se puede predecir qué hubo en x estado

backward forward

# Clase 4
19/08/25

## Modelos Ocultos de Markov (HMM): Inferencia

Probabilidad de que cierto estado haya causado cierta consecuencia dado un conjunto de observaciones.
$$ P (Q_k \space | \space O) $$
## HMM: Backward y Forward

![[Pasted image 20250819131041.png]]

O = Conjunto de observaciones
$$P(A,B) = P(A|B)$$
Backward 
Forward Estados pasados para ver la prob del futuro
Backward Estados "presentes" para ver la prob del pasado (dado que sucedio k)

## HMM: Forward

Q4: La probabilidad de que venga de Q1, Q2 o Q3

Ver los estados anteriores, sumarlos con sus observaciones y multiplicarlos

Recursicion queda de esta forma:
X * $\pi S_1$ 
Y * $\pi S_1$ 
Z * $\pi S_1$ 

 $P(O_0 | Q_0)  P(Q_0)$
	X,Y,Z	PI

Calcula un estado dado un conjunto de observaciones

## HMM: Backward

Calcula la probabilidad de un estado y haber visto observaciones hasta ese estado

K5 dado que estoy en K0

Forward parte de 0 hacia N
Backward va hacia atras, parte de N y llega hasta 0


## Algoritmo de Viterbi

Calcula los estados mas probables de acuerdo a todas las observaciones
En base a las observaciones retorna la secuencia mas probable

Calculo similar a forward, pero este toma el máximo
No suma, toma el valor máximo simplemente


# Clase 5
22/08/25

### Backward y Forward

Backward
A traves de la recursion calcula la prob de estar en un estado por observaciones pasadas 

Forward
Ver las observaciones futuras dado un estado

![[Pasted image 20250822133038.png]]

### Viterbi
Secuencia de los estados mas probables dado


## Monte Carlo
Conjunto de algoritmos computacionales que se basan en el muestreo aleatorio para obtener resultados numéricos a un problema

*Aplicaciones*
- Modelos matematicos (integrales con multiples dimensiones)
- Fisicos (difusion del calor en un espacio)
- Riesgo financiero

- Aguja de bufón
### Métodos de Monte Carlo
- Usa la generación de números aleatorios y muestreo.
- Utilizado cuando hay incertidumbre en los parámetros de entrada

1. Define el dominio de las posibles inputs
2. Genera inputs aleatoriamente dentro del dominio de acuerdo a alguna distribución de probabilidad
3. Aplica computación determinista sobre los inputs
4. Agregación final de los resultados individuales para obtener el resultado final

La aproximación depende de la cantidad de datos usados. Mientras más datos mejor

EJ 1) Cálculo de $\pi$ 

- Definir un circulo inscrito
![[Pasted image 20250822133741.png]]

![[Pasted image 20250822133752.png]]


EJ 2) probabilidad de obtener dos reyes consecutivos

1- Prob de que no existan dos reyes consecutivos

1. El dominio es mazo de 52 cartas
2. Ordenamos el mazo y lo revolvemos
3. Revisamos el mazo 
4. Si tiene 2 reyes, caso exitoso
5. Volver al punto 2

Realizar n veces 

## Filtros de Partículas

Método de Carlos pero secuencial
- Se va aplicando en cada t tiempo
- Mapea o actualiza un mapa y a la vez conocer la posición de un robot desconocida

En Monte Carlo el muestreo era estático
Para lograr la actualización del muestreo de acuerdo a un entorno de inferencia bayesiano, se aplica el *resampling* muchas veces para así converger a una aproximación de la solución buscada

Involucrado un estado de creencia que contiene incertidumbre y que se actualiza a medida que se observan cambios en el sistema.

- *Partículas*: Estado de creencia de la variable a modelar (ej. posición de un robot=
- *Mediciones*: Valores que llevan a una partícula a definir su estado (partícula esperaría a ver
- *Valores de control*: Valores que llevan a una partícula a definir su estado (lo que cada partícula esperaría ver, el robot se movió a la derecha)
- *Pesos (importancia)*: Valor cuantitativo asociado a cada partícula, que partícula es mas probable que se acerque a la medición que se han hecho

1. Inicia la distribución de partículas (conjunto) en el espacio
2. Se calcula la probabilidad proporcional de que cada partícula este representado adecuadamente al sistema basado en la observación actual.

Si tenemos 5 habitaciones en la que puede estar el robot, se manda 1 partícula a cada habitación. El robot da cierta data como temperatura, se sabe que en x pieza hay calefactor, de acuerdo a esa info, sacamos que partícula es la mas probable de que este correcto. (donde esta la estufa) y se le da cierto peso

3. Se le asigna un peso (Actualización) de acuerdo a su importancia en la observación
4. Normalizan los pesos
5. Se reasigna la distribución de puntos
6. Se introduce ruido a los valores de la partícula (valores cercanos pero no los mismos)
7. Se observa la evolución esperada del sistema en un paso (Actualizacion bayesiana, predicción)
8. Volver al punto 2

Actividad

![[Pasted image 20250822141722.png]]


# Clase 6
26/08/25

## Filtros de Kalman

- Al igual que los filtros de particulas, estiman variables de entorno con datos analíticos en vez de aleatorios
- Los errores deben distribuirse como una campana de gauss

Modelo: Dinámica del estado
La media es lo que predice el modelo, las colas la incertidumbre
$$x_k = A \cdot x_{k-1} + B \cdot u_k + w_k $$

Sensor: Mediciones
La edia es la info que nos da el sensor
$$z_k = H \cdot x_{k} +  v_k $$

> Ambas ecuaciones son lineales

Luego, la ponderación de ambas campanas genera una 3ra campana que unifica la info de ambas partes con su propia media y desviación estandar


Q: Error asociado a la 1ra campana (modelo)
R: Error por la 2da campana (sensor)
K: Indicador de que campana es más importante

Se le da mayor importancia al que tenga menor tasa de error

1. Predice (modelo)
2. Corrige (sensor)

Problemas que pueden ser usados por Kalman:
- Distribuciones Gaussianas
- Sistemas lineales
- Sistemas de tiempo discreto

Covarianza del error (que tan buena es mi medicion):
$$P_k = (I - K_K H) \cdot P^- _K$$




# Clase 7
02/09/25

## Estimadores de Máxima Similitud

Tenemos variables aleatorias y nos piden saber los parámetros 

¿Qué parámetros tiene una distribución normal?
- Media $\mu$ , Varianza 

Desconocemos la media y varianza.
¿Cómo calculamos estos valores (los más cercanos)?

Esta es la base de muchos algoritmos para calcular lo mismo.

### Distribuciones probabilísticas

1. Definir distribución de datos como cierta
	Por ej Distribución normal

2. Ver que parámetros tiene esta distribución
	Tenemos un conjunto de observaciones que son iid (variables aleatorias independientes e identicamente distribuidas).
$D = 

Parametros: $\mu = O1$ 


3.  Para determinar el máximo valor de media, varianza, derivamos

Funcion de Likelihood L 

#### Limitaciones
- Puede no ser único
- Puede NO existir
- MLE es una estimación puntual y no considera incertidumbre
- Se ajusta demasiado a los datos observados
- Overfitting (regresión, paradoja del cisne negro)


Datos -> Modelo
	 Parametros <- Entrenamiento

Sirve para Machine Learning

# Clase 8

## Algoritmo de Expectations Maximization

EJ 1) Problema: Mezcla de Gaussianas
- Parámetros: Medias, Varanzas, Pesos
- Observaciones (datos visibles): X = (1, 1.2, 4.8, 5.1)
- Variables ocultas: para cada dato observado x_n, que gaussiana lo genero
- EM:
	- Se asigna un valor aleatorio a los parámetros

MLE: $\mu, \omega$ (media, varianza) y encontrar datos ocultos (a qué gaussiana pertenece) 

1. Se asigna un valor aleatorio a los parámetros
2. 

Maximiza la probabilidad de que x parametro pertenezca a y gaussiana

EJ 3) HMM

1. Asignamos parametros aleatorios a $\pi$, T, E
2. E-Step: Backward forward
3. M-Step: Maximizar parámetros
4. Salida: valores ajustados y distribuciones de probabilidad sobre los estados en cada tiempo



# Clase 12
07/10/25

## Machine Learning

### Algoritmo de Clustering


#### TIPOS DE IA

1. Tipos de Aprendizaje
	- Aprendizaje Supervisado  
		Datos con etiquetas
	- Aprendizaje NO Supervisado 
		NO Etiquetadas
	- Aprendizaje semisupervisado 
		Con y sin etiquetas
	- Aprendizaje por refuerzo 
		Entorno Interaccion, interactuan con el entorno dando regalitos o no (Prueba y error)
	
2. Tipo de Tarea
	- Clasificación 
		AS
	- Predicción
		Valor de un departamento de acuerdo a x condiciones
	- Agrupación
		Aprendizaje NO Supervisado (ANS) y los agrupa 

EJ para 1.)
Dato: Manzana, Platano como imagen

Tratan de encontrar patrones entre las etiquetas y los datos
En base a los patrones, podrá identificar cuál es cual


**K-Means**

Tenemos una gráfica en N dimensiones, definiendo K como cantidad de clusters

2. Calcula el promedio de los valores del cluster
3. El centroide se va a mover por cada iteración hasta que los datos no cambien de cluster

Cuando tenemos 1 cluster, hay casi infinitos errores.
Mientras más clusters tenga, menor es la tasa de errores
Se detiene de agregar clusters cuando la tasa de error empieza a disminuir muy poco


07/10/25
### Mean-Shift

Los datos van migrando hacia el centro más cercano que tenga. Los clusters serán los puntos centrados, en este ejemplo 6 clusters.
La idea es migrar los puntos a los sectores de mayor densidad.

La idea es que no se especifica el valor de K a diferencia de K-means, se encuentra con T iteraciones

Necesita definir un radio, Kernel (este tiene su parámetro, llamado *bandwidth*)

- Radio $N(x)$: El radio que abarco de vecinos por cada dato
- Kernel: Cómo van a influenciar los vecinos en mi (distribución de importancia)
	- EJ) Kernel Gaussiano: los que estén más cerca les daré más importancia
	- Kernel Uniforme: A todos los vecinos les doy la misma importancia
	- *Bandwidth* $w_i$
	- 
		- Pequeño: Le doy importancia sólo a los que estén más cerca (+ Clusters)
		- Grande: a casi todos los vecinos (- Clusters)

$$ K (x, x') = e^ - \frac{||x-x'||^2}{2\delta^2}$$
(e elevado a todo)


Se itera N veces sobre cada dato hasta que converja:
1. Partimos encontrando el conjunto de vecinos (tomando cualquier dato)
	Ese dato, cuántos vecinos tiene ej: $N(x) = 3$
2. Calcula el peso para cada vecino
	Para el vecino 1, $w_1 = 2$
3. Calculo $m(x)$ para normalizarlo (divido la sumatoria por el peso)


> Útil para segmentar imágenes, también para hacer seguimientos


*¿Cuándo usar Mean-Shift?*
- Cuando no sé el valor de K (cantidad de clusters)

### DBSCAN

*Identifica Outliers*: datos atípicos

Trabaja con medidas de densidad, usando dos parámetros:

- Máx distancia $d$ para considerar vecinos
- Mínimo número de puntos $n$ para una región densa

Input


Inicializar

*Ventajas*
- NO defino el numero del cluster
- Puede tomar forma que K-Means no puede tomar (ej: carita feliz : ) )


### Agglomerative Hierarchical Clustering

Ve el cluster más cercano a otro cluster y va agrupando de menor a mayor.

- Cuando se quiere visualizar la evolución de unificar los clusters
- Usado en biología las células

### GMM

- Estimación de densidad en cualquier punto del plano (altura, peso)
- *Clasificación suave* de nuevos casos (EM) 
	- Identifica cuántas gaussianas hay
- Detección de atípicos, puntos con densidad muy baja
- Puede tomar formas más "elasticas", adaptandose mejor a los datos 

Podemos hacer predicción de datos atípicos (su prob de pertenecer a cierta gaussiana)
[!!!] Con los otros no se puede hacer






# Clase 13
10/10/25

hasta ahora se veron metodos de clustering. Hoy se vera de *predicción*, algoritmo supervisado

Entrenaremos el modelo con un conjunto, obteniendo datos nuevos con su etiqueta.

Lo importante es que haya relacion lineal entre los datos y la etiqueta 
	Los puntos sigan una tendencia lineal para encontrar la "recta" que siga su tendencia

Dimensiones -> **Predictores**

| Predictores       | Variable a predecir |
| ----------------- | ------------------- |
| X                 | Y                   |
| 2                 | 5                   |
| 3                 | 10                  |
| ?? [10/3] (media) | 15                  |
| 5                 | 30                  |

Entrenar ->
- Encontrar valores y parámetros


Pendiente $Y = mx+b$

En este caso: 
- $Y$ variable a predecir
- $x$ 1 predictor
- $m$ 1er parametro
- $b$ 2do parámetro
$$ x - \mu / \delta (media) $$

### Datos 

| Conjunto      | ¿Para qué sirve?                         |                          |
| ------------- | ---------------------------------------- | ------------------------ |
| Entrenamiento | Ajustar los parámetros del modelo        |                          |
| Validacion    | Definir Hiperparametros                  | Tasa de aprendizaje $\n$ |
| Test          | Que tan bueno es con los datos chantados |                          |

### Tutorial

1. Divide datos:
	Train / Val / Test
	70 / 15 / 15 (sólo ve los datos de entrenamiento)
2. Luego, elegir un conjunto de valores para cada hiperparámetro
3. Para cada combinación
	1. Entrenar el modelo (Train) (70 datos)
	2. Calcular métricas de qué tan bueno es el modelo (Val) (15 datos)
4. Nos quedamos con el mejor valor de hiperparámetros, *Reentrenando* el modelo (train + val) que mejor puntue en la validación
5. Evaluar modelo (test) una sola vez qué tan bueno es

## Regresión lineal Univariada
Sólo 1 predictor

$$y = ax+b$$
Reescribimos la ecuación de la siguiente forma
$$h_\theta = \theta_0 + \theta_1 x$$
- Definimos un error y buscar los valores de $\theta$ que minimicen el error
- Si tenemos m datos y el $i$-ésimo ejemplo del entremaniento $(x^{(i)}, y^{(i)})$ se define el error cuántico como sumatoria de ..

Para disminuir la tasa de error, se usa *gradiente descendiente*
-> Apunta siempre donde la función crece más -> Vector de derivadas


## Regresión lineal multivariada

Lo mismo pero con más variables

| x   | y   |
| --- | --- |
| 2   | 0   |
| 3   | 1   |
| 4   | 0   |
| 5   | 2   |


# Clase 14
14/10/25

## Regresión logística

Debiera usarse de una manera *actoada*. Al tenerse clasificacion esta vez, vamos a querer que los valores estan contenidos dentro de una franja. Se ve ahora como *umbral de decisión*


Se buscan los mejores valores para $\theta_0$ y $\theta_1$
$$h\theta(x) = \theta_0 + \theta_1x$$
(recta creciente)

$\theta_1$ dicta que tan rapido sube de 0 a 1
$\theta_0$ mueve la curva izquierda o derecha



