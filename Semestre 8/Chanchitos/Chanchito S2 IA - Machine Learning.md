
Existen distintos modelos de aprendizaje para el entrenamiento de IA

- Aprendizaje supervisado
- Aprendizaje no-supervisado
- Aprendizaje semi-supervisado
- Aprendizaje reforzado
A su vez, se separan en 3 tipos de algoritmos:
- **Clasificación**: Etiqueta discreta
- **Predicción**: Etiqueta continua
- **Agrupación**: Clustering

| Conjunto   | Funcionalidad                                                                                        |
| ---------- | ---------------------------------------------------------------------------------------------------- |
| Train      | Ajusta los parametros del modelo. Aprender preprocesamiento (imputar, escalar, codificar categorías) |
| Validacion | Elegir hiperparámetros y decisiones de modelado                                                      |
| Test       | Evalua una única vez el rendimiento final con datos nuevos/no vistos                                 |



###### ¿Por qué diferenciarlos?
Se deben ajustar según las restricciones del problema (entrada/salida) y verificar su correcta operación, dependiendo del contexto.

# Aprendizaje NO Supervisado

![[Pasted image 20251124230601.png]]



# Aprendizaje Reforzado

![[Pasted image 20251124230626.png]]



## Agrupación: Clustering
Significa literalmente agrupar. Asocia datos de características similares en grupos.

**Usos**:
- Segmentación de Mercado
- Análisis de Redes sociales
- Segmentación de Imágenes (por ej en medicina)
- Detección de anomalías

Algoritmos
- K-Means
### K-Means
Agrupación de datos bajo un cluster o grupo. Consiste en los siguientes pasos:

1. Colocar $K$ puntos en el espacio de los datos representado por los objetos a ser clasificados. 
	- Puntos se llaman **centroides iniciales**
2. Asignarle a cada objeto (dato) un grupo, representado por el **centroide más cercano**.
3. Una vez asignados todos los objetos a sus grupos respectivos se recalcula la posición del centroide del grupo.
4. Se repiten los pasos 2 y 3 hasta que no cambien de posición los centroides.

Generalmente se usa la distancia euclidiana, pero podría usarse otra como Manhattan, Coseno, etc.

El algoritmo busca que cada punto esté lo más cerca posible de su centroide. 
Lo anterior se puede interpretar que el algoritmo busca minimizar la suma de los errores cuadráticos intra-cluster, conocida como WCSS  
*(Within-Cluster Sum of Squares)*
$$ WCCS = \sum _{i=1}^{k} \sum _{x \in C_i} ||x - \mu_i||^2 $$
#### Limitaciones
1. No asegura una clasificación óptima de los objetos
2. Sensible a la distribución inicial de los centroides
3. Por lo anterior, se recomienda ejecutar el algoritmo múltiples veces seleccionando distintos centroides iniciales.
4. Buscar la configuración óptima es NP-Hard

### Mean-Shift

Basado en el uso de la moda. La moda corresponde a aquella región o valor que contien la mayor densidad de puntos.

- El mismo algoritmo determina la cantidad de clusters a través de iteraciones. No tiene una forma regular necesariamente

Necesita:
- Función para cálculo de vecinos (normalmente **distancia euclidiana**)
- Ventana probabilística o Kernel (gaussiana es la más común): K(x, x')
- Se itera N veces sobre cada punto x o hasta que converja

![[Pasted image 20251124232652.png]]


### DBSCAN
Density Based Spatial Clustering of Applications with Noise: Identifica outliers en el grupo de datos como clustering. 
**Trabaja con densidad**

Usa 2 parámetros:
- La máxima distancia $d$ entre dos puntos (antes de considerarlos vecinos)
- El mínimo numero de puntos $n$ para una region densa

La idea es que se trabaja un cluster como un conjunto de datos muy denso
- Itera sobre todos los puntos de los datos
- Si hay más de $n$ puntos dentro de un radio de $d$ alrededor mio, entonces es una región densa
	- Si se cumple, se revisa el resto de los puntos para integrar a otros puntos nuevos al cluster
- Aquellos puntos que queden fuera, se les conoce como **outliers**

![[Pasted image 20251124233153.png]]

### AHC: Agglomerative Hierarchical Clustering

Construye los clusters por medio de fusiones entre clusters más pequeños
- Ocupa enfoque **bottom-up**
- El resultado son **agrupaciones representadas en forma de árbol**
- Los clusters más grandes incluyen de forma anidada a los clusters más pequeños

Itera mientras haya más de un cluster
- Evalua todas las distancias entre clusters de a pares
- Registra las distancias entre clusters en una matriz
- Busca la menor distancia entre clusters, fusionarlos como un nuevo cluster unico y elimina ese par de la matriz

![[Pasted image 20251124233604.png]]

### GMM

Estimación de densidad en cualquier punto del plano (altura, peso)
- Clustering probabilistico, como pertenencias suaves

![[Pasted image 20251124233704.png]]



# Aprendizaje Supervisado

![[Pasted image 20251124230615.png]]


# Algoritmo de Predicción

## Regresión Lineal

Consiste en identificar tendencia de los datos observados que permitan efectuar predicción en alguna de las dimensiones de datos no procesados.

- Idea: Adelantar lo que va a pasar con respecto a cierta dimensión de análisis para x situación.
- Suponemos una **experiencia previa**, donde la etiqueta asociada a cada dato es un valor continuo (y conocido solo para los datos de entrenamiento)

Iteración 0
![[Pasted image 20251124234645.png]]

### Regresión Lineal Univariada

$x$ = variable de los datos
$y$ = etiqueta asignada a la variable $x$
relacionamos $x$ e $y$ así: $y = ax + b$, reescribiendolo como **función hipotesis**: $h_\theta = \theta_0 + \theta_1x$
Buscamos un valor de $\theta$ que minimicen el erro, determinando $\theta_0$ y $\theta_1$ que determinan la recta.
con $m$ datos

![[Pasted image 20251124234741.png]]

Definimos el error cuadratico medio.
$J$ conocido como **función de costo**, buscamos los valores de $\theta_0$ y $\theta_1$ que minimicen $J$


#### Gradiente Descendiente
Para minimizar $J$, podemos usar el **gradiente descendiente**

![[Pasted image 20251124235159.png]]

![[Pasted image 20251124235208.png]]


### Regresión Logística
Se utilizan los elementos de regresion lineal de formas distintas:
#### Función de Hipótesis
Busca generalizar y la forma en que se expresa de manera correcta. ¿Qué ocurre si es que se le ve ahora como umbral de decisión?

$$ g(z) = \frac{1}{1 + e^{-z}} $$
Una forma de usar el umbral expresado podría ser:

![[Pasted image 20251125000743.png]]

#### Función de Costo

![[Pasted image 20251125000828.png]]




# Algoritmo de Clasificación/Predicción

Clustering en KNN
Regresiones en SVM

## KNN: K-Nearest Neighbors (Supervisado)
Algoritmo que supone la **similitud** en base a la distancia de los datos
Se centra en datois conocidos previamente

$K$ es un parámetro del algoritmo y sensibiliza el resultado entregado.
Significa el número de vecinos que se consulta para determinar la naturaleza del dato actual

- El algoritmo ejecuta una votación sobre los vecinos más cercanos al nuevo dato
	- para clasificar o realizar una predicción referente a su etiqueta

#### Ejecución

1. Cargar los datos X, y  
2. Inicializar el valor del parámetro K  
3. Leer el dato a procesar (Q)  
4. Por cada ejemplo (X) en el conjunto de entrenamiento:  
	a. Calcular la distancia d entre Q y X (generalmente Euclidiana, pero puede ser alguna otra)  
	b. Almacenar d y su correspondiente referencia a X en un listado L  
5. Ordenar L, de menor a mayor, en términos de d  
6. Seleccionar las K primeras entradas de L  
7. Recuperar las etiquetas Y correspondientes a los X  
8. Si se desea clasificar a Q, retornar la moda de los Y  
9. Si se desea predecir el valor de la etiqueta de Q, retornar la media de los Y.

#### Ajuste Hiperparámetros

1. Cargar los datos X, Y  
2. Hacer split estratificado: 80% train / 20% test.  
3. Elegir candidatos de k y de otros Hiperparámetros.  
4. Hacer CV estratificada 5-fold con F1-macro (reporta también Accuracy).  
	Para cada Fold:  
	a. Ajustar Scaler solo con el train del fold y transformar train/val del fold.  
	b. Ejecutar KNN (pasos 4–9 algoritmo anterior) con cada k candidato sobre el val del fold.  
	c. Guardar la métrica.  
5. Promediar las métricas y elegir K (y el resto de hiperparámetros, si aplica).  
6. Refit del Pipeline en el train completo (80%) usando k.  
7. Evaluar en el 20% test.  
8. Para un nuevo punto Q: aplicar el Pipeline (el scaler aprendido + KNN con k).


![[Pasted image 20251125001625.png]]

## SVM: Support Vector Machine 
Similar a la construcción de la regresión. Encuentra un hiperplano que logra diferenciar la clasificación de los datos.
- Se busca que el hiperplano encontrado esté a la mayor distancia de los datos de clases distintas (mayor margen posible)

- PERO, las SVM agregan un dlc: se busca que el hiperplano encontrado esté a la mayor distancia de los datos de clases distintas **(mayor margen posible)**
	- Ayuda a que sea más fácil trabajar con nuevos datos
- Se les llama **Support Vectors** a los datos más cercanos al hiperplano buscado. 
- SVM es un algoritmo de aprendizaje supervisado y tiene **mayoritaria aplicación en clasificación**

### Conceptos Claves

![[Pasted image 20251125002635.png]]

#### SVM: Kernel

![[Pasted image 20251125002701.png]]

#### SVM: Hard Margin vs Soft Margin

![[Pasted image 20251125002815.png]]


#### SVM: Hiperparámetro C (Soft Margin)

Valor pequeño del parámetro C = penalizaciones menos estrictas por clasificación errónea = Margen grande

![[Pasted image 20251125002858.png]]

### Función Objetivo

Objetive Function = $\frac{1}{margin} + C \sum penalty$ 

### Función Hipótesis
![[Pasted image 20251125003006.png]]

Hay otras funciones como:
- Optimization Problem for SVM
- Soft Margin in Linear SVM Classifier  

### Descenso por gradiente
![[Pasted image 20251125003118.png]]



# Funciones

### Función ReLU

![[Pasted image 20251125104505.png]]

### Función Sigmoide
$$ g(z) = \frac{1}{1 + e^{-z}} $$

![[Pasted image 20251125104626.png]]

### Tanh (Tangente hiperbólica)
![[Pasted image 20251125113630.png]]
![[Pasted image 20251125113646.png]]

### Softmax
Convierte las salidas en distribucion de probabilidad. Util para clasificaciones multiples

![[Pasted image 20251125113737.png]]


