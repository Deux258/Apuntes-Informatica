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
- Ordinal: Si no lo puedo ordenar
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





