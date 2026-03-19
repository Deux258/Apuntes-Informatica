victor.reyes@udp.cl
# Clase 1
09/03/26

Objetivos:
- Recordemos cómo se realiza modelado
- Tipos de problemas
## Paso previo a los algoritmos: *Modelamiento*

### ¿Qué define el modelo de un problema?

- Una o más variables
- Dominios de cada variable (discreto o continuo)
- 0, 1 o más restricciones
- 0, 1 o más funciones objetivo (si hay puedo medir la calidad de la solución)

EJ) Crear una lata con la mayor superficie posible teniendo 128ml de volumen total.

Variables: Radio, altura
Dominios: Continuo > 0
Función objetivo: Minimizar superficie (función de las tapas y altura de la lata)
Restricción: Volumen 128ml -> $\pi r^2h$

#### Clasificación de los problemas: Dominio

1. Dominios Continuos: Dron en el aire
2. Dominio Discreto: Hospital (cantidad de camas), computación

#### Clasificación de los problemas: Restricciones

- Restringidos: Espacio para containers (limitante)
- No restringidos: Función de costo

#### Clasificación de los problemas: Objetivos

- 1 Objetivo
- Multi-objetivos
> Frontera de Pareto: Investigar la mejor solución dando mayor peso a cierta variable


## *COP* Problema de Optimización con Restricciones 

Un problema donde tengo una funcion objetivo, las variables pueden cambiar con restricciones
$$ min f(x) s.t. $$
Lo que se busca es valores en D, que cumplan con las restricciones minimizando/max lo más que se pueda $f(x)$.

## *CSP* Problema de Satisfacción con Restricciones

No hay función objetivo, no puedo medir qué tan buena es la solución (comparar), por lo que busco soluciones del problema.

## Soluciones y espacio de búsqueda

### Solución factible
asignación de variables que cumple con todas las restricciones del problema

### Solución Infactible
No cumple con las restricciones del problema. Algunos algoritmos tratan con soluciones infactibles para encontrar finalmente a través de penalizaciones una solución factible.

Una vez que llegamos a una solución factible, lo que hago es evaluar con FO y veo cuál es mejor. Si no tengo FO me quedo con las 2.
- Si es un problema de satisfacción, los limitamos a encontrar soluciones, pues no las puedo comparar

* *Espacio de búsqueda*: Espacio donde yo buscaré las soluciones


## Dificultad de los Problemas

### Problemas P
Problemas que puedan ser resueltos en tiempo polinomial por una máquina de Turing determinista.

### Problemas NP
No existe algoritmo que resuelva todos los problemas en tiempo poligonial, pero dada una solución se puede verificar en tiempo

### NP-Hard

> EJ) Job ShopScheduling Problem

Máquinas que pueden resolver tareas, con la idea de tareas puedan tener dependencias
T1 -> T5
Problema: Asignar tareas a máquinas para minimizar _makespan_ (tiempo de resolución)

> EJ) SCP

## ¿Cómo resolvemos este tipo de problemas?

- *Técnicas exactas o completas*
	Garantizan todo el espacio y siempre retorna la mejor solución (**Tiempo computacional**)
- *Técnicas de aproximación o incompletas*
	No gastan tanto tiempo, pero no garantiza la mejor solución

#### ¿Cuándo usar cada una de ellas?
Tiempo disponible para resolver el problema (o cómputo disponible).

## Técnicas Completas
4 clases

*Backtracking*
	Técnica que no usa ningún tipo de información

*Look-back y Look-Ahead* 
	Miran hacia atrás para tomar mejores decisiones


## Actividad
Diego Muñoz, Alex Marambio - Algoritmos Exactos
- Variables: 
	$D_i$ si llevo o no el juego
	$D_j$ si llevo la ropa o no
- Parámetros
	Importancia de cada articulo
	peso juegos
	peso ropa
- Dominios
	1..n ropa
	1..m juegos
	peso > 0	
- Restricciones
	Cantidad J < 6
	Cantidad R > 20
	Peso P máximo 23kg
- Funciones objetivo
Maximizar la importancia total contenida en la maleta

$$ max \sum _{i=0} ^k G_i * D +  \sum _{i=0} ^k G_j * D$$
Cuyas restricciones son:
$$ C_i < 6 \space \& \space  C_j > 20 \space \& \space P < 23kg $$
¿Cuál es el espacio de búsqueda?
2 variables con m juegos y n ropa
Juegos: $2^n$ 
Ropa: $2^m$
$$2^{m+n}$$

# Clase 2
12/03/26

- N-Reinas
- Mejora al backtracking cronológico: *CBJ Conflict Back Jumping*

## Repasito

- CSP: Problema de satisfacción con restricciones
- Variables, dominios y restricciones, sin función objetivo

- Problema N-Reinas

Posicionar en un tablero NxN, N reinas de tal forma que no se ataquen entre ellas
	- Definir variables y dominios
	- Restricciones
	- ¿Espacio de búsqueda?

Variables: ¿donde ubico la reina?
Restricciones: 2 reinas no pueden estar en la misma posición, 1 sola reina por cada fila, columna y diagonal
Espacio de búsqueda: Soluciones factibles + infactibles
: D1: 16 casillas -> $16^4$

> Dependiendo de como yo planteo la solución, puede cambiar el espacio de búsqueda

Si yo reduzco el espacio a 1 reina por cada fila -> $4⁴$

## Proceso de Búsqueda

### Búsqueda Completa
Se explora el espacio de búsqueda de manera ordenada y exhaustiva (todas).

- El proceso se termina cuando: 
	- Se encuentra una solución o todas (CSP), la óptima (COP)
	- Se demuestra que no hay solución
	- Se agotan los recursos computacionales (RAM)
	- Hay timeout (sanidad)

### Árbol
Elementos presentes:

- Estado inicial: Nodo raíz 
	Ej: tablero vacío sin reinas

- Estado: Nodo que representa la "Foto" del momento de búsqueda
	Ej: ubicación de la reina

- Acciones: A partir de un estado, que conjunto (finito) de acciones puedo realizar. Estas pueden tener un costo. Generan nodos hijos

- Nodos hojas: Solucion que cumple o no las restricciones del sistema


### Backtracking cronológico (BT)
Se realiza en profundidad para crear el arbol (fuerza bruta)

- En cada ramo del arbol hacemos una asignacion, es decir le asignamos valor a una variable o hacemos una acción dependiendo del problema.

- Cada vez que asigno debemos chequear si esta es *consistente*: Todas las otras variables tienen al menos un valor en su dominio que soporta dicha asignación.


![[Pasted image 20260312145854.png]]


## Búsqueda Informada
Buscar info de alguna forma para hacer la búsqueda más inteligente

- En el ej anterior, hay una asignación que es incompatible con todo, por lo que "condeno" en la búsqueda haciendo costos computacionales *thrashing*

¿Cómo minimizo el thrashing?

### BackJumping / Look-Back
Saltar hacia atrás a un nodo más arriba que un solo nodo

- **Look-Back**
	Hace saltos hacia atrás más eficientes / grandes (BackJumping)
	Salta a una variable responsable del bloqueo 
	No enumera algunas asignacions parciales que no conducen a una posible solución
	Para cada variable, guardar el conjunto de conflictos $Conf(x_i)$

### Backjumping dirigido por conflictos (CBJ)

- Salta a una variable responsable del bloqueo
- No enumera algunas asignacions parciales que no conducen a una posible solución
- Para cada variable, guardar el conjunto de conflictos $Conf(x_i)$
- Por cada valor erróneo, registro en Conf la variable más prematuramente instanciada y en conflicto con el intento actual de instalación

LLegamos a un camino sin salida *deadend*, debido a que existe un vacío de dominio _domain wipe-out_.

- Dado que la última variable que me da conflicto es $X_4$, retorno al nodo $X_4$ en vez de recorrer los últimos nodos


### Nogood Learning
Es una combinación de asignaciones que nunca puede llevar a una solución

Se almacenan las combinaciones de variables que no den nunca solución, y si en algún momento se llega a esa combinación de valores no se sigue buscando.

- Se puede aplicar backjumoing o backtracking 
- En base a esto, se va "aprendiendo" en la búsqueda y hay una memoria 



# Clase 3
16/03/26

## Algoritmos completos pt. 2
## Técnicas Look-Ahead
Comprenderemos la importancia de las heurísticas de selección de variable

Cuando haciamos backtracking el orden se define antes de la busqueda
Mientras más pequeño el dominio, mayor es la prob de fallar 

### Forward Checking
Pertenece a un grupo de técnicas clasificadas como Look-Ahead

Se basa en la idea de mirar hacia delante en el arbol de busqueda, para ver si al hacer una instalacion hace imposible asignarle valor a otra variable no instanciada

- Disminuye el trashing
- A pesar de que podrían existir menos nodos en el árbol, se podrían eventualmente realizar más chequeos a comparacio de otras técnicas

![[Pasted image 20260316144056.png]]

Veo las otras variables y eventualmente podría tener un *vacío de dominio para volver atrás*.
[!!] Los árboles son más pequeños, pero hago más chequeos. Con 1 ejecución basta y sobra

> ¿Qué metricas puedo tener para comparar 2 árboles?

- Velocidad (CPU)
- Cantidad de nodos
- Chequeos

Al final se mezclan las variables
¿Cuántas veces tengo que ejecutar el algoritmo para llegar a la solución?

**RESUMEN**
1. Seleccionar $X_i$ (variable)
2. Instanciar dominio
3. Razono hacia adelante
	Elimino de los dominios de las variables aun no instanciadas, los valores que no calzan con respecto a la instanciacion de acuerdo a las restricciones.
4. Si quedan valores posibles en los dominios de todas las variables por instanciar:
	1. Si $i < n$ -> Incrementar $i$ e ir al paso 1
	2. Si $i = n$ -> Retorno solución
5.  SI existe variable por instanciar sin valores posibles en su dominio, entonces retactar los efectos
	1. Si quedan valores por intentar en dominio, ir al paso 2
	2. Si no quedan valores:
		1. Si $i > 1$ -> decrementar i y volver al paso 2
		2. Si $i = 1$ -> retorno solución

> Se puede combinar con otros algoritmos. Por ej con CBJ (clase pasada):
- Reducimos dominios hacia delante
- Si llegamos al deadend, hacemos salto a la variable con el conflicto

¿Es siempre FC mejor que un BT simple?
	Para ciertos problemas pueden ser igual de costosos, o incluso FC más costoso que BT
	Si todos los valores son compatibles, super caro FC
	En tiempo incluso BT puede ser más rápido dependiendo del problema

### MFC - Lazy Forward Checking

Es más flojo, chequea las variables hasta que encuentra el más adecuado y pasar rápidamente a una solución

La gracia es que no reviso todo para problemas super grandes.
- De esta manera, eventualmente podríamos detectar vacios de dominio (igual que FC) pero sin tantos chequeos
- Sigue siendo completo

### Orden de Instanciación
El orden en el cual son instanciadas las variables afecta el tamaño del árbol de búsqueda 
-> desempeño del algoritmo de búsqueda

#### *Heurísticas de selección variable*
Tecnica que selecciona variables
-> No es costoso, usa info del momento para construir una instancia

> En general están basadas en la premisa *fail-first*, para tener éxito, se debe intentar primero en donde más probablemente se fallará

Entre más info usemos, mejor funcionará pero a mayor costo de CPU (trade-off)

Algunos ejemplos:
- *Dom* Menor dominio
- *Dom+Deg*: Lo mismo pero si hay empate se elige que tenga más restricciones
- *Dom/Deg*: Aquella que minimiza el cuociente dom/deg

En general, depende del problema.

- Restart: Empezar todo de nuevo con distinto orden

### Técnicas de Preproceso: Consistencia de Argos y Nodos

- Todo CSP/COP puede ser transformado en un problema binario
- Todo CSP/COP con restricciones binarias puede ser modelado a través de un grafo

Con lo anterior, podemos aplicar técnicas de preproceso para CSP/COP
-> Nodo consistencia, arco consistencia, camino consistencia

Arco consistencia -> Pregunto si hay algun valor que cumpla la restriccion entre 2 nodos antes de ver el nodo consistencia













