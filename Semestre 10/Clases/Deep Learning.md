# Clase 1
17/08/26

*Objetivo* -> Recorddar fundamentos de ML (Clasificacion binaria)

- Funcion de hipotesis
- Funcion de perdida vs Funcion de costo
- Gradiente descendente
- Vectorizacion
## ML: Clasificacion binaria

Lo que queremos: ¿Es brisket?
Lo que hace el modelo -> $y = \{0,1\}$

- Puede ser multiclase

La x es un vector ya que puedo tener varias variables
- Para cada x voy a tener una etiqueta $y$
- Usaremos *matrices* para los ejemplos
	- Procesamiento para *paralelizar*

### Regresión Logística

Dado un input $x$, queremos una funcion que permita predecir $y$ conociendo a priori la etiqueta real. Que tome las x y lo lleve a y (ideal que calce con la etiqueta real)

El problema es acotar el espacio de busqueda 

$ŷ = \theta^t x + \theta_0$
$\theta$ = Parametro, es un vector
$\theta_0$ = 

En vez de lo anterior se propone usar
$$ ŷ = T (\theta^t x + \theta_0) $$
La ventaja es que esta acotado (funcion de euler) entre 0 y 1
El problema es que ocurre el fenomeno de *desvanecimiento*, dificil de designar si es 0 o 1

#### Tagente de Hiperbólica
Mejora directa de la funcion de euler

### Función de perdida/costo
La idea es generalizar mi data, donde a partir de mis ejemplos empiezo a entrenar a mi modelo, ajustandolo a traves de costos
Se usa porcentaje de division 98%, 1%, 1%

¿*Por que se divide en 3*?
- Entrada 
- Validacion -> Ajusto los hiperparametros
- Test -> 
Para no introducir sesgos (overfitting)

La función de costo tenemos que medir si va bien o no, y para esto usamos 
**ECM** Error cuadratico medio

$$ L (ŷ, y) = ½ (ŷ-y)$$
El problema es que para este contexto no funciona bien, como va entre 0 y 1 da un resultado muy pequeño dificil de medir y *convexidad*
> Casi imposible salir del mínimo local

Alternativa: **Binary Cross-Entropy**
Mide el error para clasificacion binaria

$$  L (ŷ, y) = -(y log ŷ + (1-y) log (1-ŷ)) $$
Para el conjunto de datos es la sumatoria

### Gradiente Descendente
Para mejorar la optimizacion global

Buscamos ahora los valores de $\theta$ y de $\theta_0$ para minimizar $J(\theta, \theta_0)$

- Designo $\alpha$ para moverme en el gradiente. *Hiperparametro*
- El problema es que el valor es fijo, puedo moverme muy lento o muy rapido y pasarme de largo.

Es parecido a una red neuronal 

![[Pasted image 20260817120148.png]]

L: Cuanto tengo que propagar el error hacia atras?

y: Etiqueta real
a: Estimada (funcion de hipotesis a partir de $\sigma$)
m: 

El problema de esto es que se ejecuta secuencialmente

### Vectorizacion computacional

La idea es parametrizar modelos enormes usando matrices.
La ventaja a nivel computacionale es enorme (200 veces mas rapido)

Regresion logistica vectorizada se usa en todas partes

![[Pasted image 20260817121717.png]]

Lo mismo pero paralelizado y en matrices.
Sigue teniendo el mismo problema de que se ejecuta N veces *no hay forma de paralelizar*

### Actividad

Regresion logistica $(x_1, x_2, y)$
Ejemplos: (1,1,0), (1,2,1), (2,2,0)
Parametros luego de una iteracion

$\theta_0=1$
$\theta_1=2$
$\theta_2=3$




