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


# Clase 2

Motivacion -> Resolver problemas no lineales a traves de machine learning

## Red Neuronal

Capa de input -> Capas ocultas (Funcion de activacion) -> Capa de salida -> Y

Problema de tener muchas capas ocultas -> Si complejizo mucho la funcion se ajusta demasiado a los datos. *Overfitting*

parametros -> conexiones e input

En cada neurona puede tener $\theta_x$ y ademas su propio $\theta_0$

![[Pasted image 20260820114517.png]]

En este ejemplo tengo 21 parametros

> ¿Por qué es tan importante saber Redes neuronales?

Se usa en todas partes, sobre todo para deep learning (2-layer -NN) 

Proceso los datos de izquierda a derecha *feed-forward*
 *Feed-back* -> En un paso intermedio genero otra entrada a la red, teniendo $X_n$ entradas y $Y_n$ salidas, usado en **RN**

Basicamente tengo una suma ponderada $\theta^T + \theta_0$ = $Z$, donde $a = ŷ$


### Notación
$(i)$ -> Ejemplo o dato
$[I]$ -> Cierta capa del modelo
Subindice -> Referencia a neurona

$\theta_1^{[1]}$ = capa 1 entrando a la neurona 1
$\theta_{02}^{[1]}$ = Neurona 2 referenciando a $\theta_0$ de la capa 1
$Z_i^{1}$ = 1 Suma ponderada de la capa 1

Aprovecha poder de computo para procesar todo esto a traves de matrices.

![[Pasted image 20260820115916.png]]


EJ) $Z_1^{[2]} = \theta_1^{[2]T} a^{[1]} + \theta_{01}^{[2]}$ 
T = Transpuesta (para que calce la multiplicacion)

![[Pasted image 20260820120516.png]]

Es lo mismo pero agrupando todo
$Z$ = Calculabamos la suma ponderada para todas las neuronas (4 sumas de $a$)
Matriz $W$ = Todos los pesos de la red
- 4x3 Son los pesos que entran, 4 filas y 3 columnas (3 entradas)
- Todos los pesos de la primera parte de la red (12)

$a$ = Salida -> Cada uno de las neuronas tiene una salida (4 salidas)

Cada $W$ hace referencia al peso de cada neurona 

> Tenemos que incluir los datos, porque aun no paralelizamos nada

Todo esto me sirve para procesar datos
- Tengo un dato, con eso obtengo a y retorna $ŷ$. Con esto obtengo el $y$ real
- Puedo aplicarlo para m datos
-> El *problema* es que sigue siendo lineal

Vemos *vectorización* para paralelizar datos

- Lo único que cambia es que agrego otra letra $X^{[1](i)}$ (i)
- Puedo comparar $ŷ^{(1)} -> y$ 


### Vectorización

![[Pasted image 20260820121523.png]]


### Funciones de Activación

- ReLU
- Lineal -> La suma ponderada 
- Leaky
- Softmax -> Cuando quiero clasificar y tengo mas de 2 etiquetas
	- $e^{Z} / \sum e^Z$  

![[Pasted image 20260820121833.png]]

LeakyReLU ayuda a ajustar mejor la recta que uno desee. Depende mucho del tipo de prueba que uses.

#### TAREA
- $e^{Z/T} / \sum e^{Z/T}$   ¿Cual es la ventaja de tener como hiperparámetro la *temperatura*?
- AutoML -> Libreria para ajustar hiperparámetros de forma automática. ¿Cómo funciona?
!!! No es tan buena pero sirve de ayuda


#### Pregunta
Si nos encontramos resolviendo un problema complejo y con relaciones no lineales entre las variables, ¿Qué ocurre si solo usamos funciones de activación lineales?

-> La respuesta queda una función lineal. La red neuronal se puede reducir a un solo nodo
Por eso se usan funciones de activación no lineales



