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




