
# Regularización

- ¿Qué es?
Técnica que permite mitigar el overfitting. Funciona en base a ajuste de importancia de cada característica que se emplean en los modelos (theta)


perceptrton > Neuorona
MLP
MultiLayer Perceptron



# ANN
Resuelve problemas de aprendizaje automático, prediciendo a partir de grandes volúmenes de datos.

- Capa de entrada
- Capa oculta
- Capa de salida

![[Pasted image 20251118164253.png]]

# MPL
Forma más simple de ANN

- No tiene memoria ni estructura temporal
![[Pasted image 20251118164424.png]]

![[Pasted image 20251118164500.png]]

### Funciones de Activación
- Sigmoide 1-0
- TAN 1- -1
- RELU < 0 = 0, > 0 es el numero
- SoftMax


# BackPropagation
Usado para ajustar los pesos entre neuronas

![[Pasted image 20251118164618.png]]


![[Pasted image 20251118164641.png]]



## Funciones de Activación

![[Pasted image 20251118164758.png]]

![[Pasted image 20251118164736.png]]



# Clasificacion



# Paradigmas de aprendizaje

- Aprendizaje supervisado
- "" No supervisado
- Semi-supervisado
- Reforzado

Se separan en 2 tipos 
- Clasificacion 
- Prediccion
- Generación

![[Pasted image 20251118165439.png]]

![[Pasted image 20251118165448.png]]

![[Pasted image 20251118165502.png]]

Con recompensa



## NO supervisado
### Clustering
Agrupar datos de características similares

### K-Means
El algoritmo consiste en la agrupación de datos bajo un cluster o grupo.  
Consiste en los siguientes pasos:  
1. Colocar K puntos en el espacio de datos representado por los objetos a  
ser clasificados. Estos puntos se denominan los centroides iniciales.  
2. Asignarle a cada objeto (dato) un grupo, representado por el centroide  
más cercano.  
3. Una vez asignados todos los objetos a sus grupos respectivos se recalcula  
la posición del centroide del grupo.  
4. Se repiten los pasos 2 y 3 hasta que los centroides no cambien de  
posición.

**Limitantes**
1. No se asegura una clasificación óptima de los objetos.  
2. Es sensible a la distribución inicial de los centroides.  
3. Por lo anterior, se recomienda ejecutar el algoritmo múltiples veces  
seleccionando distintos centroides iniciales.  
4. Buscar la configuración óptima es NP-Hard.

### Mean-Shift

![[Pasted image 20251118165706.png]]

![[Pasted image 20251118165735.png]]

![[Pasted image 20251118165745.png]]

	
![[Pasted image 20251118165812.png]]

![[Pasted image 20251118165825.png]]

![[Pasted image 20251118165842.png]]


# Predicción
## Regresión Lineal

