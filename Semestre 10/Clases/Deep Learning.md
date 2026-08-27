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


# Clase 3
24/08/26

## Tarea

Uso de red neuronal -> Usar modelos clasicos de 1er curso

1ra parte
- No tiene que funcionar tan bien
- La idea es usar 2 modelos clásicos y a partir de eso analizar el problema y con eso implementar una red neuronal
	- !!! Cuando dice implementar una red neuronal, es buscar uno a partir de experimentos, el que tenga mejor resultado es el que se usara.
- Todas las decisiones de diseño debe estar en el código

2da parte
- 2 herramientas para mejorar el funcoonamiento de busqueda de hiperparámetros
	- Arquitecture search (NAS) y AutoML

3ra parte
- Generar data sintética

Hacer video con presentación del código - 20m estándar
De que se trata el problema 


## Ajuste de Hiperparámetros

El ajuste de hiperparámetros es clave para el exito
### Back Propagation

Equivalente a lo visto en clase 2 pero retrocede por nivel
- Se realiza el proceso de vectorización para aprovechar el hardware disponible

El problema es que si tengo millones de datos se complica la ejecucion del programa.
- Se divide por lotes para ajustar los datos. 
- *1 epoca*/iteración es cuando paso por todos los datos
- PROBLEMA -> Tiene que ser un buen muestreo pq si tengo solo un tipo de ejemplo pierdo información

- Si divido los lotes en espacios más pequeños, *gradiente estocástico*,  se ajusta demasiado y retorna ruido basicamente. No asegura convergencia

### DNN: Red neuronal profunda
Tengo muchas capas ocultas, eso es todo (normalmente más de 5)

1. Entrenamiento
2. Validación -> Uso otro conjunto de datos no usado previamente para validar si da error o no


Underfitting -> El modelo tiene que ser complejizado, hay un error más de fondo
Overfitting -> Ajuste de hiperparámetros
Error excesivo -> Estás en problemas

### Parámetros vs Hiperparámetros

Parámetros = Pesos del modelo, los que se ajustan a partir de los datos
HIperparametros = Valores definidos por el que está creando el modelo
- Tasa de aprendizaje, capas ocultas, neuronas ocultas, funciones de activación a usar

*A aprender*: Momentum, tamaño de batch, parámetros de regularización, entre otros

Dado x problema, ¿Qué hiperparámetros debo utilizar?

Algo que se hace comunmente, es entrenar a valores cercanos e ir cambiando los valores
Me voy quedando con la conf que me de el resultado más cercano perturbando los valores iniciales de a poco 
$$ (x,y) => (x', y')$$

![[Pasted image 20260824120536.png]]

Eje y: Función de costo
Eje x: Epocas

La idea es minimizar el costo -> PROBLEMA gasta mucho tiempo en prueba y error. 

Optimizador famoso -> *Adam* Estándar de deep learning 

### Entrenamiento, Validación, Prueba
El conjunto de datos se separa en 3 conjuntos 

ML tradicional -> 60/20/20 % pensando para 10.000 ejemplos
	Para 1.000.000 20% puede ser excesivo
Deep Learning -> 98/1/1 % o una variante de esto

- El conjunto debe tener un orignel igual o similar (misma distribución)
	Si son de fuentes distintas, puede funcionar bien en x contexto y mal en otro

1. Entrenamiento 
	Se entrenan diferentes modelos (distintos hiperparámetros) con el conjunto de entrenamiento y se usa el conjuunto de validación para ver cuál funciona mejor.


![[Pasted image 20260824121859.png]]


Ejemplos:
- Error de entrenamiento 1%, Error de validación 15% *overfitting*
- Error de entrenamiento 15%, Error de validación 16% *underfitting*
- Error de entrenamiento 15%, Error de validación 30% *Mezcla de escenarios*
- Error de entrenamiento 0.5%, Error de validación 1% *Tamos bien*

[!!!] Depende mucho de lo que yo esté evaluando el porcentaje de error está bien o no

### Flujo de ML/DL

1. En el peor caso de underfitting -> Tengo que cambiar el modelo/arquitectura
2. Overfitting -> Hartas formas de arreglar eso
3. Ideal tener hartos datos -> Con pocos es más posible tener overfitting
4. Si no tenemos ninguno -> Bkn

#### Regularización
Mitigar el *overfitting*

**Función de costo**: Penaliza los errores

Los dos tipos de regularización más conocidas
- L1 -> Vector $\theta$ queda sparse (cae casi a 0)
- L2  (mas usado) decaen los pesos

A los $\theta_0$ NUNCA se le aplica costo o cambio

#### Dropout

![[Pasted image 20260824123037.png]]

Ciertas conexiones basadas en una probabilidad de la red no son consideraras.
- *Solo entrenamiento*, en otras fases genera ruido
- *Funciona* debido a que no hay dependencia con algunas pocas características, los pesos se distribuyen.

Otros tipos de regularización
##### Aumento de Datos
![[Pasted image 20260824123315.png]]

##### Early Stopping

![[Pasted image 20260824123337.png]]


# Clase 4
27/08/26

Clase pasada
- Proceso de entrenamiento, validación y testeo en DNNs
- Overfitting vs underfitting
## Entrenamiento y Optimizadores

### Normalización de los conjuntos de entrenamiento

1. Restar el promedio, calcular = $1/m \sum x^(i)$ y luego $x = x-\mu$ 
2. Normalizar con varianza, calcular 

*Basicamente*
Uno calcula el promedio de los datos y centro los datos en el promedio
En vez de tener una estructura cualquiera, todos se centran de manera regular

> Yo normalizo pero *sólo en entrenamiento*

Es como si estuviera datos sin probarlos realmente, ajustando el modelo a mi ventaja
	Validación y test NO se pueden tocar

![[Pasted image 20260827114151.png]]

Hay otro con min-max pero usaremos este que se vió en clase.
- Normalizar conjunto de datos para la tarea

### Inicialización de los Pesos
Dependiendo de las funciones de activación que yo use, es cómo se inicializan los datos para x capa.

Por ej para ReLU -> desaparición y exploción de gradiente. 
	Para evitar eso, debo probar bien los pesos y parámetros para que no ocurran estos problemas

### Algoritmos de optimización
Buscamos la mejor velocidad de entrenamiento. La vectorización ayuda a paralelizar los datos, pero qué pasa si $m >> 10.000.000$? 

**Solución** -> Dividir el conjunto  de entrenamiento en "*mini-batches*", por ej de $2.000$ datos
1 época permitiría realizar 5.000 gradientes descendentes

![[Pasted image 20260827115056.png]]

- SGD = mini-batch

> La 2da gráfica teóricamente es mejor que lo de la izquierda. ¿Por qué?

1. La tendencia siempre baja en la 1ra, mucho más probable que uno se estanque en un óptimo local
2. En el 2do, un ruido bueno puede escapar de un óptimo local (no asegura converger) pero ayuda a avanzar mejor con 

### EWAs Exponentially Weighted Averages
Para entrenamiento

![[Pasted image 20260827115605.png]]

Saca la tendencia de los datos ponderando los datos + el pasado.

- Se calcula $Vt = βv_{t-1} + (1-β)x_t$ 
- La idea es sacar promedio ponderando lo que tenga más peso recientemente

$\beta$ = hiperparámetro -> Importancia de los datos
$x$ = Dato que estoy analizando
$V_0$ = Condición inicial 
	Si $V_0$ = 0 -> $V_1$ = $βv_0 + (1-β)x_1$ 


El pasado lo vas olvidando pero sigue acumulándose
Idealmente NO usar $V_0$ = 0 (depende del caso pero mi tendencia debe partir casi a la misma altura que mis datos)

#### Para la mejora
En vez de x guarde mis datos, almacene los gradientes 

Si sigo la tendencia de los gradeintes, los recientes tendrán más peso que los pasados, para en el fondo seguir una tendencia hacia el mínimo local en vez de tener algo muy loco

![[Pasted image 20260827120806.png]]

Anterior, el rojo
El mejorado guardando el gradiente el amarillo

Corrección: $ṽt =vt /(1-β)t$

### Gradiente acelerado de Nesterov
La gracia es que es muy parecido, pero mira hacia delante. 

![[Pasted image 20260827121212.png]]

Para no hacer error, calculo mi paso próximo calculndo el error y aplico correxión al punto donde saltaría más adelante para llegar más rápido al mínimo local.

### RMSprop
Muy parecido al anterior, pero con la diferencia de que guarda la magnitud de los gradientes (antes guardaba la dirección), para ver cuánto tengo que moverme en *cada dimensión del espacio*.

![[Pasted image 20260827121326.png]]

- Para aquellos que tienen gradientes grandes, los pasos son más pequeños
- En cambio un gradiente pequeño, el efecto que aplica es que va a aumentar el paso en esa dimensión 
- NO dependo del $\alpha$ para calcular el próximo paso

### ADAM
Mezcla tanto del momentum con el algoritmo anterior

Guarda la dirección + cantidad del gradiente
Momentum -> RMSprop -> corección -> actualización de peso

![[Pasted image 20260827121640.png]]

Quizás no sea el mejor pero depende del caso


### Decaimiento de la tasa de aprendizaje


![[Pasted image 20260827122036.png]]

### BatchNorm
Normalizar por lotes
¿Qué hago yo si tengo lotes para entrenar? Tendria que sacar un $\mu, \sigma$ por cada lote

¿Qué valor de $\mu, sigma$ uso para validación y test? -> PROMEDIO