# Clase 1
09/03/26

## Tipos de Machine Learning

- unsupervised Learning
- Supervised Learning
- Reinforcemet Learning

![[Pasted image 20260309131501.png]]


## La necesidad de Estandarización

1. Reproducibilidad
	Aseguro que llos resultados no sean accidentales
2. Escalabilidad
	Permito que el proyecto crezca de forma ordenada
3. Colaboración
	Lenguaje común para equipos multidisciplinarios (otras carreras)

## KDD Knowledge Discovery In Databases

![[Pasted image 20260309132008.png]]

Puedo volver al paso anterior, es un proceso iterativo

¿Por qué proceso datos?
	Rara vez recibo datos como yo los quiero para el modelo (ej: edad, doy 23 años pero doy mi fecha de nacimiento al sistema)

## OSEMN
Estandar que viene a ser lo mismo

![[Pasted image 20260309132403.png]]

Obtain: Obtengo los datos
Scrub: Limpio los datos
Explore: Exploro que es lo que necesito (encontrar patrones)
Model: 
Interpret

## El Estándar de la Industria: *CRISP-DM*
Cross-industry Standard Process for Data Mining (80% falla, el 20% paga las cuentas)

Respondo los problemas de negocio con minería de datos

1. Entendimiento de la empresa
2. Entendimiento de Datos
3. Preparación de datos
4. Modelado
5. Evaluación
6. Despliegue

*MDE* son los datos en una empresa grande:
- Data warehouse (cosa bonita)
- Late warehouse (excel a csv)

El *Gobierno de datos* es el encargado de traducir el negocio a algo como MDE

Si me falta algo lo puedo agregar a mi flujo de data science


## Ciclo de Vida del Producto (ML Life Cycle)
Construir, desplegar y mantener modelos de machine learning

![[Pasted image 20260309133414.png]]

## Data Science es una intersección Disciplinaria

![[Pasted image 20260309133739.png]]

## Roles en la Industria

Data scientist 
	Encargado de todo el flujo y analisis de un proyecto de ML. Recibe la data para sus analisis desde los Ingenieros de datos y lo entrega al cliente con una interpretación

Data Science Manager

Data Architect
	Define el stack tecnológico y arquitectura de soluciones técnicas de Machine Learning
  
Data Engineer
	El que conecta el gobierno de datos con los flujos de framework, básicamente de la disponibilidad de los datos.

Machine Learning Engineer
	Despliega modelos de IA que permiten a las maquinas aprender a predecir correctamente. Sólo modela

Data Analyst
	Suele ser un rol más junior. Realiza analisis que no requieran de un modelo de ML, encargado de visualización en Dashboards o proveer datos al resto de la empresa.

Statistician
	Es un ML Engineer pero que viene seco para la matemática,. Suele trabajar de la mano con el resto del equipo y acuden a el cuando toda esperanza es vana.

Data Analytics Manager
	Hace hablar y trabajar al resto de personajes, suele ser DS con más experiencia manejando wnes



# Clase 2
12/03/26

## Obtención y fuentes de datos

Sin datos limpios, ni el mejor modelo sirve

### Tres esferas de Datos
Toolkit del Data Scientist:

1. Fuentes Internacionales
2. Fuentes Nacionales / Gubernamentales
3. Creación de Propias fuentes

#### 1. Fuentes Internacionales

- Google Research: https://research.google/resources/datasets/
- Kaggle: https://www.kaggle.com/datasets
- UC Irvine: https://archive.ics.uci.edu/

Kaggle
Token creado:
KGAT_a9e5d30c0e61686c2e4f0352beb15e09

![[Pasted image 20260312132004.png]]

#### 2. Fuentes Nacionales / Gubernamentales

- https://datos.gob.cl 
- Mercado público: https://api.mercadopublico.cl/default.aspx
- Banco central: https://si3.bcentral.cl/Siete/es/Siete/API

#### 3. Propias Fuentes
Tutorial

1. WebScraping
2. BDD en la Empresa / Institución
3. Cámara en su bolsillo

Dataframe es como una matriz pero con índices tanto en las filas como columnas



heart_disease_df_.info(5)
hheart_diseade_df_describe(5)


# Clase 3
16/03/26

## Preprocesamiento de Datos Pt. 1

### La ciencia de datos es *GIGO*
> Garbage In - Garbage Out

Datos erróneos -> Resultados incorrectos

El preprocesamiento es una perte del flujo de ML donde el analista agrega valor.
Hay muy poco desarrollado en forma automática y los datos suelen tener errores o vicios que deben ser tratados.

### Diferencia entre Datos e Información

Los datos hacen referencia al almacenamiento (persistente o no) de aspectos sentados de la realidad

La info es la cantidad medible de conocimiento, basado en datos y tiene un contexto.

1. Datos
2. Limpios en una base de datos
3. Analizado
4. Representados de forma visual
5. Explicados con una historia

![[Pasted image 20260316131459.png]]


### Cantidad de Información
#### Alta Entropía 
Alta Incertidumbre
-> Se necesita más info para describir el sistema. Todos los resultados son igualmente probables

#### Baja Entropía 
Baja Incertidumbre
-> Se necesita menos info. Algunos resultados son más probables que otros.

Entropía = 0 -> Totalmente predecible
Varianza


### "Tipos" de Datos

![[Pasted image 20260316132045.png]]

Categóricos o Numéricos
> El hecho de que un dato sea un *int*, no significa que sea numérico

Numérico
- Discreto (enteros)
- Continuos (infinito)

Categórico
- Ordinal: Si lo puedo ordenar
- Nominal: NO lo puedo ordenar

### Problemas con los Datos

1. Datos Faltantes
2. Datos Incorrectos
3. Datos Inútiles (o poco utiles)


#### 1. Datos Faltantes

1. MCAR: Perdido completamente random
2. MAR: Perdido random (existe relación)
3. MNAR: Perdido no random

###### MCAR: Missing Completely At Random
La data perdida está distribuida de forma aleatoria (uniforme) y no relacionada con otras variables del dataset.
###### MAR: Missing At Random
Hay relacion entre los datos perdidos y existentes

**SOLUCION**
Imputar usando la info de las otras variables
- Máxima verosimilitud
- KNN
###### MNAR: Missing Not At Random
NO es random, pero no tengo ningún otro dato para relacionar y difiere sistematicamente de los datos observados y es No-Ignorable

**SOLUCION**
- Marcado AD-HOC
- Depende
- Encontrar más data

#### 2. Datos Incorrectos

1. **OOR** Datos fuera de rango
	*SOLUCION* -> Tratar como un missing value, Imputación iterativa

2. Data ruidosa
	

3. Inconsistencia de formato


# Clase 4
19/03/26

## Preprocesamiento de Datos Pt. 2
breve resumen:

Pasar los datos de
realidad -> *sensor* -> Dataset

### Problemas con los Datos

Existen 3 tipos de problemas:
1. Datos faltantes
2. Datos incorrectos
3. Datos inútiles (o poco útiles)
#### 3. Datos inútiles

1. Features completamente concentrados
2. Outliers Unidimensionales y Multidimensionales
3. Skewed numerical features
4. Multi-colinealidad
5. Informacion Leakage

##### 1. Features concentrados

Por qué no me sirven datos demasiado centralizados?
-> Por la entropía, no me da información relevante

**SOLUCIÓN** 
- Matar la variable

##### 2. Outliers
Son datos atípicos (no malo). En muchos casos es exactamente lo que se busca

**SOLUCIÓN**
- Eliminar la variable
- Mantener y tener cuidado con las normalizaciones (ej: min_max_scaler)

> Unidimensional:

Diagnóstico unidimensional
- Visual con boxplots
- IQR


![[Pasted image 20260319133254.png]]

> Multidimensional:

Diagnóstico Multidimensional:
- Isolation Forest
- ECOD

![[Pasted image 20260319133321.png]]


##### 3. Atributos Numéricos de alta Asimetría
PROXIMAMENTE

##### 4. Multi Colinealidad
La covarianza entre 2 variables dividido en la desviación estandar de una variable multiplicado por la desviacion estandar de la otra.

![[Pasted image 20260319134208.png]]

Tipos de correlaciones:

![[Pasted image 20260319134333.png]]


Básicamente son características que estan muy correlacionadas entre sí.
NO confundir con una alta correlación contra la variable target en un modelo supervisado, eso es deseable.

Diagnóstico
- Matriz de correlaciones
- Scatterplot

**SOLUCIÓN**
- Dejar sólo una de las variables correlacionadas
- Reducción dimensional

##### 5. Information Leakage
De todos los problemas que pueden tener los datos, ESTE es el peor
-> Culpa del data science

Cuando aparece un dato que no debería de estar ahí porque se agregó externamente.
Pasa en un modelo supervisado cuando tenemos variables predictoras xl que son dependientes del target Y

Es decir:
$$ Y = F(x) + E \space donde \space X = {x1, x2, x(Y)}, ..., xn $$

Si aparece un dato Y, depende del target 

Diagnóstico
- Modelo sospechosamente bueno
- Feature Importance

**SOLUCIÓN**
- Eliminar variables xl
- Jugar con los tiempos (skip) del modelo entre las variables X e Y

> ¿Cómo saber si tiene alguna relacion el modelo con Y?

1. Correlación entre X e Y (se mueven a la misma dirección)
2. Si el atributo es categórico -> $X_i ^2$ (dependencia)
3. Si el X, Y es numérico -> Probar con Test Fisher o K-S

$Y$ NO depende de las variables dependientes como lo son x
Importante saber interpretar en base al contexto

Cuando uno tiene un modelo que involucra el tiempo
- Entreno con datos del pasado para predecir el futuro



# Clase 5
23/03/26

En una gráfica Madurez en función del tiempo:
1. Descriptiva
2. Diagnostica
3. Predictiva
4. Prescriptiva
## Análisis exploratorio de datos EDA (clases pasadas)

> Cálculo de estadísticas

- Media
- Moda
- Varianza
- Desviación típica
- Q1, Q2, Q3 = P25, P50, P75
- Observaciones duplicadas
- Nulos etc..

## Estudio de Distribuciones

### 1. Modalidad
1. Modalidad
2. Bimodal
3. Trimodal

![[Pasted image 20260323132530.png]]

> Skewness o Asimetría

![[Pasted image 20260323132518.png]]

#### Kurtosis

![[Pasted image 20260323132736.png]]

#### Atributos numéricos de Alta Asimetría
Datos Inútiles

Corresponde a casos donde la distribución de los datos está cargada hacia la izquierda (alta asimetría)

Diagnóstico:
- Histograma
- Skewness

**SOLUCIÓN**
- Logaritmo: $Log(X_i + k)$
- Box-cow, Ext. Yeo-johnson

### 2. Análisis Exploratorio de Datos
¿Cuáles son las relaciones entre variables?

![[Pasted image 20260323133322.png]]

Los categóricos no los puedo meter aquí, por lo que creo valores relacionales

![[Pasted image 20260323133446.png]]

> Relación con el objetivo

![[Pasted image 20260323133858.png]]


Pero realmente, ¿Qué es lo que yo quiero predecir?
-> Depende de los datos. Los datos siempre mandan sobre el modelo

### 4. Análisis y Construcción del Target

Preguntas
- ¿Qué queremos hacer?
- Tenemos el label? Cuánto tenemos
	Datasets
- Si no tenemos datos, los podemos comprar, conseguir?
- Revisar desvalance de clases
- Revisar temporalidad de los labels

Undersampling vs Oversampling

![[Pasted image 20260323135521.png]]


# Clase 6
26/03/26
## Transformación de Datos

> Preprocesamiento -> Datos limpios
> Transformación -> Alimentar un modelo

Es la etapa del proceso de Machine Learning, posterior al Análisis Exploratorio de Datos y al Srub o limpieza, donde se acomodan los datos para que un modelo los reciba de la mejor forma posible.

![[Pasted image 20260326131113.png]]

Sesgo <--> Varianza
Interpretabilidad <--> Performance Predictivo

Preprocesamiento (eliminar)
Transformar (agregar)

- Variables Categórica Nominal
- 
### Variables Categórica Nominal

Teniendo Categórica Nominal (ej: color) -> transformarlo de una forma "legible" para el modelo

- One-hot Encoder
- Dummy encoding (elimina la redundancia, ej elimina la columna que sobra)

### Variables Categóricas Ordinales
- Ordinal Encoding

| Original Encoding | Ordinal Encodign |
| ----------------- | ---------------- |
| Poor              | 1                |
| Good              | 2                |
| Very Good         | 3                |
| Excellent         | 4                |

- Target Encoding

![[Pasted image 20260326132320.png]]
![[Pasted image 20260326132331.png]]

Reemplaza el valor categorico por un numero, mejorando el modelo

### Atributos numéricos de Alta simetría

![[Pasted image 20260326133114.png]]



¿Como saber si mejora o empeora el modelo?
Por el tipo de distribución

Probablemente al inicio el modelo no esté correctamente implementado, si no que tiene que ejecutarse 300-500 veces para q funcione correctamente

Box-Cow

![[Pasted image 20260326133214.png|697]]

Yeo-Johnson (pan de dios)

![[Pasted image 20260326133202.png]]

El eje x no es nada, dificil sacar interpretacion para el humano, pero más fácil para el sistema

### Transformación de Variables Numéricas
Transformaciones típicas en variables numéricas:
- Distribuciones Asimétricas
- Normalización y Escalamiento 
	- Min Max Scaler

$$ \frac{ x - x_{min}}{x_{max} - x_{min}}$$
![[Pasted image 20260326134626.png]]

Problemas: Outliers -> el máximo sería gigante, por lo tanto dañaria la gráfica

- Estandarización

![[Pasted image 20260326134805.png]]

![[Pasted image 20260326134906.png]]

PROBLEMA: La distribucion podria no tener nada que ver con la normalización

![[Pasted image 20260326135456.png]]

![[Pasted image 20260326135919.png]]


- Ser su propio jefe
Euristicas / Algoritmos propios 
EJ) RFM

![[Pasted image 20260326140612.png]]





# Clase 6
30/03/26

## Modelos de Clasificación - Machine Learning

![[Pasted image 20260330132730.png]]

### Supervisado
1. Clasificación
2. Regresión
3. Forecasting
### No Supervisado

1. Clustering
2. Dimensionality Reduction


#### Clasificación

##### *Regresión Logística*
Genera una curva sigmoide

Estima la probabilidad de que una observación pertenezca a una clase usando la función sigmoide (logit)
El algoritmo ajusta los betas para que se asemejen a la recta

![[Pasted image 20260330133429.png]]


##### *K-Nearest NeighBors (KNB)*

Clases que estén cerca (Parecido a lo visto en IA)
Clasifica un punto basandose en los K vecinos más cercanos (métricas de distancia) en el espacio de características

![[Pasted image 20260330133605.png]]


##### *Support Vector Machines - SVM(IA)* 

Encuentra un hiperplano optimo para separar clases en datos complejos. El hiperplano puede no ser lineal

Transformo el espacio por kernels -> Agregamos una dimensión para separar los planos

![[Pasted image 20260330133905.png]]

![[Pasted image 20260330133917.png]]



##### *Random Forest*
Abren sus ramas por entropía 
Construye múltiples arboles de decisión aleatorios y combina sus predicciones para mejorar la precisión y reducir el sobre-ajuste

![[Pasted image 20260330135129.png]]

##### *Gradient Boosting*

Basado en árboles de decisión, donde cada árbol aprende de los errores del anterior, Se denominan modelos ensamblados
- XGBoost
- Light GBM

![[Pasted image 20260330135148.png]]




# Clase 8
02/04/26

## Medidas de Performance

### Curva ROC y AUC
Dudar cuando la curva es demasiado perfecta

**ROC**
Es la representación gráfica de la habilidad de un modelo para distinguir entre las dos clases. 

**AUC**
Representa qué también el modelo distingue entre clases en comparación con un modelo aleatorio. Un valor de AUC = 0.5 indica un desempeño similar al azar, mientras que AUC = 1 sugiere una excelente capacidad de discriminación.

![[Pasted image 20260402135322.png]]

¿maximizar o minimizar?
En todos los casos busco maximizar 

Accuracy -> Maximizar
Precision -> Maximizar
Recall -> maximizar
F1 Score -> maximizar

### Binary Cross Entropy

Mide la precisión de un modelo al comparar las probabilidades predichas con las clases verdaderas matemáticamente

Se calcula sumando el logaritmo  negativo de las probabilidades predichas para cada clase verdadera. Especialmente útil porque penaliza fuertemente las predicciones erróneas con alta certeza.

![[Pasted image 20260402135830.png|473]]



# Clase 12
09/04/26

## ForeCasting
Predicción del futuro 

## Series de Tiempo
Son una categoría de Machine Learning enfocada en analizar y predecir *datos secuenciales*.

A diferencia de los modelos tradicionales, el orden de los datos es fundamental. Para hacer predicciones, estos modelos aprenden patrones de la serie histórica y consideran tendencias, estacionalidad y fluctuaciones aleatorias.

> App de Clima

- Implica analizar datos que cambian con el tiempo y aplicar modelos estadísticos para predecir patrones y tendencias futuras.
- Los datos se ordenan cronológicamente creando una relación secuencial.
- Cada observación depende de observaciones anteriores

## Componentes

1. *Tendencia*
	Dirección o tendencia positiva o negativa a lo largo del tiempo
2. *Estacionalidad*
	Patrones que se repiten en intervalos fijos dentro de una serie de datos
3. *Ruido*
	Info impredecible de los datos que se escapa de conceptos como la tendencias y estacionalidad

![[Pasted image 20260409131758.png]]

imagen: Estacionalidad, tendencia, ruido

### Estacionariedad

- Media y varianza se mantiene constante
- No hay tendencia ni estacionalidad
- Autocorrelación constante

![[Pasted image 20260409132259.png]]


-> La varianza no es constante

### Diferenciación
Transformar la serie en una que representa los cambios (incrementos o decrementos) entre periodos consecutivos


![[Pasted image 20260409135404.png]]

Resumen:
- Darse cuenta del tipo de problema
- Si no tiene tiempo, es regresión (al menos q tenga clasificacion)

# Clase 13
13/04/26


## Nodos / Unidad para Funciones de Activación

![[Pasted image 20260413133453.png]]

![[Pasted image 20260413133503.png]]


- Reset Gate
- Actualización
- Candidata
- Salida

## Redes Neuronales


![[Pasted image 20260413133703.png]]



### LSTM

![[Pasted image 20260413135217.png]]

- Olvido (forget, f)
- Sigmoide
n 





# Pre-Solemne 1
16/04/26


1. Entendiendo que estos son los datos oficiales de la compañía financiera, cuál de las
siguientes afirmaciones es correcta.

A) Al no pertenecer a una fuente validada como Kaggle o UCI ML Repository esta
información no debería usarse para desarrollar un modelo, y sería recomendable
acceder a nuevos datos a través de de una API.
R: medio feka

B) Sería inutil realizar un EDA y preprocesamiento ya que es la data oficial así que
incluso si hay errores debemos usar esta.
R: Se puede visualizar al menos

C) Podemos solicitar al departamento de de T.I de la compañía que desarrolle nuevas
variables de necesitarlas en el modelo.
R: El que tiene responsabilidad de analisis, tambien de modificarlo

D) Sería recomendable realizar un EDA para poder descartar problemas en la data, en
caso de encontrarlas podemos realizar las transformaciones nosotros como
analistas.
R: *CORRECTO*. Es recomendable

E) Deberíamos realizar data augmentation con IA generativa para hacer denoising de la
data.
R: Baiteo historico



2. Ud realiza una revisión de los datos que le provee la institución financiera, y
encuentra que el rango de la variable edad hay algunos casos con 126 años. ¿Cuál
sería su conclusión al respecto?

A) Son outliers unidimensionales, revisaría si hay relación con la variable
objetivo usado K-S antes de eliminar la variable
R: Muy buena práctica, pero el dato por defecto es 1/1/1900

B) Son outliers multidimensionales usaría isolation forest para confirmarlos y los
eliminaría
C) Son datos fuera de rango, los trataría como un valor nulo e imputaría usando
K-NN (K nearest Neighbors)
*CORRECTO*

D) Son datos correctos, no por ser un número grande significa que está mal,
sobre todo temas de crédito no es bueno discriminar por edad
E) Son datos nulos de tipo MNAR imputaría por la media



![[Pasted image 20260416132238.png]]


R: A

![[Pasted image 20260416132734.png]]

R:D


![[Pasted image 20260416133058.png]]
![[Pasted image 20260416133117.png]]

R: B (no queremos ids en los modelos)

A: No necesariamente hay data leakash
C: Super buena práctica, pero no es para este caso. 
D: Es categórico pero sigue siendo ID - Agarra una categorica, compara en la distribución y coloca un número optimo en vez de la categoría como tal

![[Pasted image 20260416134137.png]]

R: B

![[Pasted image 20260416135728.png]]

R: E

Un poquito de esto y más de esto -> *Desbalance de clases*
A: Target 1 y 0, Categorías (si es perrito o no), por lo que no es razonable plantearlo como target numérico
B: Si, pero no puedo usar accuracy porque el modelo miente, dice que estamos bien cuando este se encuentra desbalanceado (por la proporción). Si fuera 50/50 tendría sentido accuracy
C y D: 
E: F-1 Score es promedio entre precision y recall (recall lo contrario a precisión)


---

# Clase 14
30/04/26

La que determina que algoritmo usar o modelo es a través de la F.O.

Modelos NO Supervisados:
1. Clustering
2. Reducción Dimensional
3. Reglas de Asociación

## No Supervisado - *Clustering*

Agrupar datos similares en función de sus características o patrones. No existe target para este tipo de modelos.

## Modelos Típicos para Clustering

### K-Means
Algoritmo de clustering. Basado en distancias *sensible a outliers*.
La primera iteración 

### Hierarchical Clustering (Jerarquico)

Enfoque jerarquico que trata cada punto de datos como un clúster individual y fusiona iterativamente los pares mas cercanos hasta formar un unico gran cluster. No requiere K inicialmente.


### DBSCAN

El más fuerza bruta pero el más efectivo para realizar segmentaciones asimétricas.
Agrupa puntos densamente empaquetados en el espacio continuo y marca como ruido os puntos aislados en reguines de baja densidad. (*covid*)

- Epsilon: El radio de busqueda topologica
- minPoints: Densidad minima requerida dentro del minimo requerido dentro del radio Epsilon para formar un núcleo

> No tiene problema de Outliers

### SOM / Mapas de Kohonen

Asigna clusteres a grupos de daos con patrones similares a traves de arquitectura de redes neuronales artificiales.

Mapea datos de alta dimensionalidad en una cuadricula bidimensional, preservando la topologia original del espacio de características

#### Requerimientos
- Mecanismos: Aprendizaje Competitivo (neuronas compiten por activarse)
- Casos: Extracción de características complejas, reconocimiento de patrones

Cartografia que trata de capturar x topologia.

### Neural Network Clustering



# Clase 15
11/05/26

## Métricas de Clustering

### Métrica del Codo - Elbow Plot
No se llama codo -> WCSS

Es el punto de inflección de la curva entre la cantidad de clusters K y la norma de las distancias a la media en cada cluster.

Sumatoria de la distancia de cada centroide para cada cluster, por lo que itero
_NO se puede hacer con DBSCAN_

### Silueta
Funciona para todos
Revisa 2 cosas: Calidad del cluster y qué tan bueno es el clúster consigo mismo

Calcula la bondad de ajuste de un modelo de clustering al comparar la distancia intracluster respecto de las distancias intercluster.

- Si están todos los puntos mezclados, el resultado < 0 (menor)

### Callinsky Harabanz
Criterio de la Razón de Varianza.
Es la razón entre la dispersión entre clústeres y la dispersión dentro de cada clúster.

- Mientras más alto sea el valor, mejor es la calidad de los clusters

$$CH = \frac{Varianza \space Inter-Cluster (Separacion)}{Varianza \space Intra-Cluster (Cohesion)} $$


Inter-Cluster -> Separacion de diferentes clusters
Intra-Cluster -> Cohesion dentro de un mismo cluster

> Mientras más abajo mejor

Es *unbound* -> Mientras más alto el valor mejor, NO tengo un valor perfecto

### Davies-Bouldan
Calcula la similitud promedio entre cada cluster y su cluster más parecido.
Lo ideal es que los grupos sean lo más distintos posibles entre sí. Una similitud baja es el resultado óptimo (0).

$$R = \frac{Dispersion \space Intra-Cluster}{Separacion \space Inter-Cluster} $$

Si hay un óptimo al cual llegar = 0




# Clase 16
14/05/26


Modelos No supervisados
## Reducción Dimensional

Reduce el número de variables en un cconjunto de datos, manteniendo la mayor cantidad de información.

### Motivación
Un modelo con gran volumen de variables se vuelve cada vez más dependiente de los datoss con los que fue entrenado (sobreajuste)

Cuanto menos variables tenga nuestra muestra de entrenamiento, menos supuestos hará nuestro modelo y será más sencillo o menos complejo.

1. Eficiencia Computacional
2. Visualización
3. Disminuye


Contengo la misma cantidad de información, encuentro patrones que a simple vista no se ven. Simplifica los datos conservando la mayor cantidad posible de información.

Algoritmos:
### PCA: Principal Component Analysis
Método estadístico que permite simplificar la complejidad de espacios muestrales con muchas dimensiones a la vez que conserva su información.

Tengo que escalar para hacer PCA e interpretarlo correctamente. JAMAS te avisa

- PCA calcula bmedia y varianza de las variables, y direcciones de máxima varianza (componentes).
- Deja de ser una tabla a un gráfico de puntos
- PROBLEMA: *Es lineal* -> No captura todos los patrones que no sean lineales (*no lo puedo saber*)
- Parecido a K-Means

Bueno, Bonito, Balatro

### T-SNE
Calcula la probabilidad de que pares de puntos de datos en el espacio de alta dimensión estén relacionados y luego elige una incrustación de baja dimensión que produzca una distribución similar.

- Destruye la forma pero permite realizar clasificaciones posteriores
- *!! Asquerosamente lento* -> Muestra de datos

EJ) T-SNE para imágenes, detección de numeros -> DBSCAN + clustering
### Autoencoders
Redes neuronales enseñadas a comprimir datos y luego reconstruirlos.

Input $X$->Encoder -> Feature *Z* (espacio latente) -> Decoder -> Output $^X$

Busco un error$E_R$ mínimo


















