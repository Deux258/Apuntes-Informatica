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
- A pesar de que podrían existir menos nodos en el árbol, se podrían eventualmente realizar más chequeos a comparación de otras técnicas

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


# Clase 4
19703/26

## Problemas Continuos

### Elementos de los problemas
- Variables y dominios
- Función objetivo
- Una o más restricciones

Para esto, se busca generar técnicas que resuelvan este tipo de problemas

**Técnicas**
-> *Interval Branch & Bound*
Tecnicas complejas que resuelvan problemas continuos (muy complejos)

Para los problemas infinitos, el computador tiende a aproximar a finitos
Probablemente falle

Tienes que pensar que el computador siempre está aproximando, por lo que se toma con "pinzas" las soluciones otorgadas como *rango de soluciones*

### En busca del óptimo global
La única forma de tener una técnica completa -> Búsqueda a través de árboles

No puedo hacer asignaciones a variables!! los dominios son continuos
*Gran problema*: Tengo que mostrar en la solución que el computador otorga un resultado aproximado

### Aritmética de Intervalos
Aritmética especial que sirve para manipular colecciones de valores

**Sobreestimar**: Cuando yo agrego más valores de lo que realmente toma 

![[Pasted image 20260319144820.png]]

Suma: [0,12] Sobreestimado: [-1, 13]

Uso los rangos completos para evaluar los restricciones. Tengo que usar un intervalo de valores

![[Pasted image 20260319144920.png]]

[0, 25] + [-6, 10] + [4, 4] = [3, 39]

#### Algunos Conceptos Clave

- Ancho del intervalo wid(x)=ub(x)-lb(x). Ejemplo: wid([-3,9])=9-(-3)=12

### Interval Branch & Bound

La idea para solucionar continuos, divide el espacio de búsqueda en áreas

![[Pasted image 20260319145421.png]]

Azul: Soluciones factibles
Amarillo: Soluciones infactibles
El óptimo global del problema es la estrella

uno parte creando nodos dividiendolo *Bisección* (entre 1 y 2) es binaria. Divido el dominio de x

¿Qué variable tengo que elegir para dividir?
- Tratas de dividir donde los problemas nuevos sean mas simples que el completo

Heurística de selección variable 
-> El problema es que mira la información actual simplemente

2. Los marcos negros se llaman *filtrados*, elimina de manera continua todos los valores que están fuera

Busco soluciones que estén dentro del rango establecido para encontrar los límites

*Bound*: Cortar o podar

DIBUJO

### Bisección

- Consiste en dividir el dominio de una de las variables en el punto medio, creando 2 nuevos nodos (cajas)
- Se buscan esencialmente 2 cosas
	1. Al dividir que los nuevos problemas sean más fáciles de resolver que el original
	2. Fallar rápido en la búsqueda
- Existen actualmente 3 tipos de Heurísticas:
	1. Largest-First
	2. Round-Robin
	3. Basadas en Smear

### Upper Bounding
Buscar soluciones para podar"

Usar metaurística dentro de cada nodo, soluciones factiles (mínimos locales)

### Selección de Nodo
Técnicas de aprendizaje 

### Software
- *Ibex*: Librería de código abierto en C++

> 3 técnicas importantes de búsqueda:
### Beam-Search
Técnica incompleta
- Busca las K mejores, sólo los nodos más prometedores se consideran en cada nivel del árbol
- Usa el parámetro w, el cual representa el número de  "beams" que consideramos

¿Cómo las elige? Algún tipo de decisión (tema de investigación)
### Monte Carlo Tree Search
Técnica incompleta
- Usado en juegos en tiempo real, problemas de optimizacion como transporte, scheduling, entre otros.
Toma un nodo prometedor, expande una decisión y a partir de eso hago una simulación y propago esa respuesta

### A-Star
> Google Maps


# Clase 5
23/03/26

## Algoritmos de Aproximación / Metahurística

Algoritmos Greedy: Deterministas y Estocásticos

### Técnicas de Resolución
Área donde ya no hay garantía de optimización 
-> Ya no hay problemas con el espacio de búsqueda (*tradeoff*)

- El tiempo de cómputo es mucho menor
- *Técnica Estocástica*: Aleatorio
	- Positivo: Busca distintas áreas del problema
	- Negativo: No me garantiza buen resultado

> Ejecuto muchas veces, no tengo garantizado resultado pero puede buscar en espacios enormes.

- Se puede adoptar a cualquier problema

![[Pasted image 20260323144046.png]]


> Algoritmos de Búsqueda Incompletos:

*Heurística*: Ordenado

- Diseñado para un problema en específico
- Usan algún info del problema
- Para resolver un problema rápidamente

Siempre llega a la solución y termina ahi

*Metaheurísticas*: Desordenado

Esquema general  que busca por zonas prometedoras para encontrar la solución

- [Trayectoria]: Una solución que cambia en el tiempo. Cuando llega explota. haciendo una búsqueda exhaustiva
- [Población]: Hay varias que se mueven en el espacio. Sirve para explorar más pero son significativamente más costosos

- Usan heurísticas para buscar/construir soluciones

**PROBLEMA**: Requiere de tiempo para poder ajustar sus parámetros


> Existen 2 tipos de técnicas incompletas:
1. [Constructivas]
	- No requieren de una solución inicial
	- Van construyendo una solución asignando iterativametne valores a las variables del problema
	- Manejan soluciones parciales (hecho a la mitad)
Parten de nada y construyen a medias

2. [Preturbadoras]
	- Requieren de varias soluciones iniciales (o 1).
	- Modifica una solución: Aplico un movimiento -> o función de vecindario
	- Maneja soluciones completas
Parten de algo ya construido para solución completa


#### Que hace un greedy
Encontrar rápidamente una solución lo más rápido posible Para dsp pasárselo a una técnica *perturbadora*

Evitar determinista para un metaheuristico poblacional,

**PROBLEMA**: Se centra en la foto del momento, me perjudica a largo plazo.

### Requisitos Para Greedy

- *Representación*: Interpretación de la estructura de la solución
- *Función de Evaluación o Miope*: Tengo que ver lo que tengo en el momento porque no veo más allá

-> Determinista: Siempre llega a la misma solución
-> Estocástico: Asignar probabilidad en base a ganancia (random pero electivo)


### GRASP
Metaheurística de Trayectoria

1. Es un Greedy Estocástico
2. Búsqueda local: Algoritmo que solo hace explotación (Hill- Climbing)
3. Cuando construyo la solución, exploto hasta un punto donde no mejoro más
4. Empiezo nuevamente la búsqueda local
5. Tengo que guardar en memoria la mejor solución para no hacer cualquier cosa
- Barato
- (-) Pierde información

Básicamente Greedy -> GRASP

¿Cuándo me detengo? -> Tiempo o Iteraciones o que se estanque

### !!! A tomar en cuenta
Metaheurística, Árbol.

- Metaheurística -> Cuando el problema es dificil y el espacio es grande
- Árbol -> Problema pequeño pero complejo
- Siempre los greedy llega a una solución buena pero ciega (no mira más allá)



# Clase 7: Charla ricolina
30/03/26

## Estrategias Adaptativas de Reinicio y Clustering Para Branch And Bound Mediante Q-Learning

- Problemas de Optimización Numérica con Restricciones (NCOP)

### Interval Branch And Bound
Dibujo exotico del profe
-> Sirve para problemas infinitos

1. Seleccion del nodo
2. Bisección
3. Fittro y Poda
4. Upper Bounding

### Reinicio + Clustering
*Posible solución*: Reinicio adaptativo que interviene durante la ejecución de B&B cuando hay signos de bajo rendimiento, usando algoritmos de agrupamiento

### Reorganización del Buffer

Envuelvo y trato de descartar N nodos en 1 solo paso en vez de revisar los N nodos uno por uno para posiblemente no encontrar solución alguna. El problema es saber cuándo ocuparlo o cuando saber que está correcto.

Vuelvo a empezar desde un punto intermedio para un nuevo espacio de búsqueda, con tal de investigar de otra forma el espacio de búsqueda.
No conviene envolver todo, sino con un criterio ojala acotado

*PROBLEMAS*
1. Al ojo: Valores arbitrarios reactivos (basados en criterios heuristicos), designados a       K-Means cada vez que se reinicia
2. DB-Scan: Alto costo computacional
3. Se podría juntar de nuevo los espacios descartados como si fueran los espacios a buscar, sensible a *Outliers*

### Estado del Arte
Aprendizaje de Politicas internas
- Seleccion de nodos
- Poda Agresiva
- Selección de Variables de Ramificación

Busca optimizar la ruta de búsqueda en cada paso, usando ML para mejorar las heurísticas.

## Aprendizaje Reforzado
Rama de la IA en la que un agente aprende a tomar decisiones mediante la interacción con un entorno dinámico. 

- No requiere de dataset - No es supervisado
- Modelado a través de los procesos de decisión de Markov.
- Aprende mientras soluciona

Agente -> Ambiente -> Accion -> Recomensa 

### Q-Learning
Recompensa acumulada por las acciones

- Aprendizaje por diferencia temporal que busca maximizar la función Q -> utilidad de realizar una accion especifica en un estado determinado

Para el contexto del problema es reiniciar o no, y los estados se refieren a cosas del problema que me dicen si reinicio o no.

#### Propuesta
(foto exotica)


### Procesos de Decisión de Markov

1. Estados
	- Tasa de estancamiento
	- Tamaño del buffer
	- Calidad de rendimiento
	- Eficiencia inmediata
2. Acciones
	- Continuar busqueda 
	- Reiniciar
3. Recompensa/Castigo
	- Mejora de UB
	- Convergencia
	- Outliers
	- Costo por paso
	- Reinicio activado
	- Rechazo de Hulls


### Recompensas
Diseñada para entrenar al agente a priorizar la calidad y velocidad, forzando la eficiencia. Si es valor negativo castigo pal agente

- Overfitting -> Evito generalización
- Random Seed
- No hay receta para crear estados para saber si están buenos 
- Hiperparámetros


# Clase 7
02/04/26

- Hill-Climbing Mejor-Mejora
- Hill-Climbing Alguna-Mejora
- Restarts en Hill-Climbing
## Recordar

### Metaheuristicas
no garantiza encontrar la mejor solucion pero el tiempo computacional es razonable para encontrar la solución.

Se aplican a distintos dominios como biologia, fisica, produccion, data mining, etc.
Si el problema es facil, aweonao si usas metaheuristicas.

Aplicar para todo en adelante:
- *Exploración* / Diversificación
	Busca zonas prometedoras, busco lugares buenos donde haya soluciones.
- *Explotación* / Intensificación
	Busco en una zona particular/centrada buenas soluciones intensamente (ya no exploro)


![[Pasted image 20260402144330.png]]

Después de explotar, ¿Qué hago?
-> Si se estanca, definir hiperparámetros
-> Cambiar algo del algoritmo para escapar y explorar otros puntos del dominio

## Hill Climbing
Búsqueda local. MH de trayectoria o solución única. Solamente explora.
La idea es mejorar a partir de una solución ya construida.

*Perturbativas*: La solución ya está construida
*Constructoras*: 

- Hill Climbing es perturbativa
- A través de operadores de movimiento, se va mejorando dicha solución, buscando que el valor de la función objetivo de dicha solución sea mejor que la solución actual.
- Busco la solución más cercana 

> ¿Cómo manejar soluciones infactibles?

Necesito función objetivo, aplico *penalización* $f_{obj} - \theta (x)$
-> Penalizo según cuantas restricciones se están contradiciendo


### Búsqueda local

![[Pasted image 20260402145740.png]]

No hay derivada porque computacionalmente es muy caro

### *Receta*

necesito
- Una función objetivo  que mida la calidad de solución
- Uno o más movimientos que permita recorrer el vecindario (lo invento yo) 1 o más
	- Un criterio para seleccionar la variable que se va a modificar
	- Un criterio para elegir un valor para esa variable seleccionada
Más de 1 operador de movimiento me da variación

- A través de operadores de movimiento, se va mejorando la solucion
- elijo la mejor (aplicando función objetivo)


## Hill Climbing Mejor-Mejora

1. *Inicialización*: Crear una solución a partir de algún criterio heurístico o aleatorio
2. Mientras no se cumpla el criterio de parada (no hay mejora, tiempo, iteraciones)
	1. Genero vecindario a partir del movimiento elegido y conservar la mejor solución del vecindario como solución actual
3. Mostrar solución + valor F.O. + tiempo

La mejor del vecindario

## Hill Climbing Alguna-Mejora

Genero vecinos de a uno y la primera que genere mejor me muevo ahí

1. En algunas ocasiones nos encontraremos con problemas en el que el vecindario de una solución es muy grande
2. En tal caso, solo generamos el vecindario hasta el punto de encontrar la primera solución que mejore la actual

## Hill Climbing con Restart

Para evitar estancarse con optimos locales, recomienzo el algoritmo con una nueva solución cuando este se encuentre estancado.

Cada vez que hago restart se olvida de la memoria, *desde 0*

La idea es aplicar un greedy estocastico para tener resultados variados, no determinista
> SOLO EXPLOTA

### Escape de óptimos locales
Además del restart, la otra forma de escapar es aceptar soluciones que empeoren la calidad de la solución actual

*PROBLEMA*: Puedo entrar en un ciclo
SOLUCIÓN -> [Tabu Search] Para evitar ciclos


##### Ejercicio para reflexionar un sábado/domingo en la tarde, ojalá con brisket

-  Supongamos que tenemos el problema de las 4-Reinas y queremos encontrar una solución, pero usando una técnica como Hill Climbing.
-  ¿Cómo lo haría?

Problema de satisfacción -> Hay que inventar F.O. para llegar a realizar Hill Climbing


# Clase 8
06/04/26

> Mejora de HC!!
## Tabu Search
Tiene lista tabu que permite aceptar movimientos que empeoraran la solucion actual para encontrar algo mejor.

Puede salir del optimo local para buscar el optimo global

Largo para que pueda explorar más cc                                                                                                       

# Clase 9
09/04/26

Algoritmos:
## Simulated Annealing (SA)
De Trayectoria

Escapa del óptimo local con probabilidades. Inspitado en termodinámica

- Inspirado en el trabajo Metropolits et al. 1953 en el campo de termodinámica estadística

La idea es cuando algo tiene cambio de temperatura, la energía se empieza a mover (átomos) y a medida que baja la temperatura llega a un punto de equilibrio. Se lleva esta idea a algoritmo.

La gracia es que acepta cosas peores. A través de una probabilidad dada por 2 cosas:
- Temperatura
- Calidad de F.O.

Dado ambos existira  una probabilidad de posible mejor solución 

### Idea
- Permite movimientos a soluciones que empeoren la F.O para escapar de óptimos locales.

### Probabilidad de Aceptación y Temperatura
Distribución de Boltzmann

![[Pasted image 20260409144132.png]]

En base al $\Delta$ acepto cosas malas

Cuando T es muy alto, la prob tiende a 1
T es bajo, la prob tiende a 0

- A cierta temperatura, hago varios intentos de nuevas soluciones
- La temperatura siempre va decayendo con ciertos tipos de reglas
- Lo ultimo no me asegura que sea lo mejor. Guardo el mejor individuo en base al vecindario que yo creé (como tabu search)

### Algoritmo general

1. Se genera la solución inicial (greedy aleatorio)
2. Se repite N iteraciones manteniendo la misma temperatura
3. Si yo mejoro la solucion actual, puedo cambiar la temperatura (posibilidad)

Cuando defino temperatura mínima y se llega a esta, el algoritmo termina

Decisiones:
- Temperatura inicial
- Condicion de equilibrio
- Temperatura minima
- Cuánto baja la temperatura (update)

Si quiero configurar es mucho mas caro pq tengo que modificar variables


### *Ingredientes de SA*
- Todo lo que tiene HC
	- Representación
	- Evaluación
	- Operadores de vecindario
- Función de prob de aceptación (Boltzmann)
- Temperatura inicial y final
- Proceso de enfriamiento: Clave para la eficiencia y efectividad del algoritmo
	Importante que dure harto

### Aceptación de movimientos
La prob de aceptacion de un movimiento que no mejora l solución actual es:

$$ P(\Delta_{obj}, T) > R$$
R num aleatorio entre 0 y 1

T alta -> Me muevo aceptando soluciones malas
T baja -> Me muevo solo si tengo una mejora (poca prob a moverme a soluciones malas)

### Estado de Equilibrio
2 mecanismos para saber cuándo actualizar temperatura

**Estándar:** Tener un numero N. Despues de N iteraciones modifico la temperatura

¿Cuántas iteraciones? -> debo analizar el vecindario para decidir. 

**Adaptativo/Técnica Online:** Depende de la F.O. Puede cambiar según los parámetros que encuentre.

Técnica Online -> Cuando empiezo a buscar algo en durante una ejecución
Técnica Offline -> Definido desde el inicio

### Enfriamiento
Tenemos 2 condiciones sobre la temperatura

- T>0 para todo i
- El límite cuando i -> $\infty$ de $T_i$ debe ser 0.  

La temperatura se puede actualizar de 3 formas:

![[Pasted image 20260409150349.png]]

Si la geometrica le doy un valor muy alto, puede que demore mucho en buscar posible solución.

### Condiciones de Término

- Llegar a una temperatura final (popular) tiene que ser baja por ej 0.01
- Tiempo
- N iteraciones
- Estancamiento

¿Cómo yo digo que tan bien o mal funciona mi técnica?
-> Promedio
-> Variación estándar
-> Gráfico de iteraciones vs Función objetivo

> Múy util cuando es discreto, con continuas no funciona tan bien


## Otros algoritmos: ILS
Son de nicho, usado muy poco, de trayectoria

Dada una solución $s'$, se aplica una perturbación (random-walk) y a esa solución nueva aplico búsqueda local.

-  Cuando llego al espacio nuevo, aplico búsqueda local HC $s''$
- Veo si cumple con los criterios
- Si $s''$ es mejor que $s'$, voy al nuevo. Si no me quedo donde mismo y aplico otra perturbación.
- Es *random* pero *simple*

## LNS - Large Neighborhood Search
Destroy and repair. *Restart con información parcial*

Destruye la solución y reconstruye. 
- Hago un greedy y construyo una solución en x espacio de búsqueda.
- Cuando llego al optimo global, aplico método que destruye parte de la solución que tengo 
- Cuando aplico greedy a la solución incompleta, llego a otra cosa. 
- Básicamente mejoro la solución que tenía existente con el nuevo greedy

![[Pasted image 20260409152329.png]]



---

# Clase 11
11/05/26

## Algoritmos Evolutivos Pt. 2

Todos parten de conjunto de soluciones iniciales $P_0$. La idea es que la poblacion vaya mejorando con el tiempo (generaciones).
Mejoran con 2 operadores, Cruzamiento y Mutación

La idea es que aquellos que tengan fines buenos tienen mayor prob de cruzamiento e ira mejorando hasta encontrar la solución óptima.

### *Pseudocódigo general*

1. Genero una población inicial N
2. Evalúo todos los individuos de la pob. Guardo la mejor solución.
3. Mientras no se cumpla el criterio de término (converge)
	1. Elijo 2 individuos
		1. Torneo
		2. Ruleta
	2. Defino si se hará mutación (probabilidad) con los hijos creados en 1.
	3. Agrego hijos a la nueva población.
	4. Cuando se tengan N nuevos individuos:
		1. Generaciones++, reemplazar población (segun criterio)
		2. Actualizar a mejor solución
		3. Volver a 1.
	5. Se entregan los resultados de la ejecución.


Ahora vemos algoritmos de nicho, como:

### Differential Evolution (DE)
Solo sirve para *problemas continuos*. Corresponde a otro algoritmo evolutivo. Menos popular que GA pero que muestra buenos resultados en optimización continua

Al igual que GA, DE genera una población inicial de soluciones $P_0$ de tamaño $k$. Cada individuo corresponde a un vector real $x_{ij}$ de dimensión $D$.

Cada individuo es codificado como un vector de números de punto flotante. Cada elemento del vector $x_{ij}$ es generado aleatoriamente en el rango $x^j_l, x^i_u$ lo que representa el *lower y upper bound* de cada variable.


La recombinación/cruzamiento funciona de forma distinta a GA. Este se basa en un operador que realiza una combinación lineal.

- Mayor costo por más cantidad de variables a tener en cuenta

![[Pasted image 20260511145822.png]]

- Elige una dimensión de forma aleatoria
- El potencial es que trabaja con soluciones que son continuas


![[Pasted image 20260511145626.png]]

- Si la nueva solucion tiene mejor fitness la remplazo y si no la mantengo


## Algoritmos de Coevolución Cooperativa

Problema en común que beneficia a todos, donde se toma la estrategia de "evolucionar" en conjunto.

Puedo tener un problema grande que lo pueda dividir en pequeñas partes resolviendolo con distintas metaheuristicas para construir una solución más grande. [!!] No se ve mucho

*PROBLEMAS*: Sincronización, paralelización, costo computacional

¿Dónde aplicarlo? -> Redes neuronales o donde pueda paralelizar


### Scatter Search 
(no se abrevia) Algoritmo super caro evolutivo que hace búsqueda local. Algoritmo de población + trayectoria. Entrega soluciones muy buenas

Solucion de tamaño 100 y de este saco 10 individuos *conjunto de referencia* para mantener diversidad

1. Poblacion inicial
2. Poblacion mejorada 
	Búsqueda local - Hill Climbing para cada individuo - Genero 100 soluciones
3. Reference set
	De esos 100 tomo 10
4. Subsets
	Todas las combinaciones las cruzo y evaluo si son mejores que las que ya tenia
5. Generated solution
6. Improved generated solution
	Búsqueda local
7. Vuelvo al punto 3 
	Se pierden las 90 soluciones que trabajé inicialmente



# Clase 12
14/05/26

## Algoritmos de Inteligencia de Enjambre

Algoritmos que se inspiran en el comportamiento de especies, como *hormigas*, abejas, peces, aves, murciélago, entre otros.

- Nacen del comportamiento social de estas especie para competir por la comida
- La característica principal es la "cooperación" por *comunicación indirecta*, para así ejecutar movimientos en el espacio de búsqueda

> Categoría: MH de Poblaciones

- Son evolutivos -> Gen0, Gen1, ..., GenN
- También hay componente de un *líder*, que hace de guía para el resto de animales

Propuesto por James Kennedy y Russel Eberhart - Inspirado en movimientos de las bandadas de aves. Propuesto inicialmente para *problemas continuos*. La comunicación entre agentes maneja diversificación e intensificación.


## Particle Swarm Optimization - PSO

- Cada partícula $i$ es una solución candidata al problema y es representada por$x_i$
- Tiene 2 componentes principales ($x_i, v_i$)
	1. Posición $x_i$
	2. Velocidad $v_i$ -> Indica la dirección de vuelo y el paso

- Algoritmo cooperativo, en el sentido que las mejores partículas influyen en el comportamiento de sus compañeras.

Hago una predicción del movimiento a la nueva posición de la partícula en base a la velocidad.

![[Pasted image 20260514144343.png]]


Hacia me estoy moviendo es influido por 2 cosas:
1. Lider
2. Lo mejor que ha hecho la partícula

> El líder puede cambiar, dependiendo de la solución que encuentre la partícula (defino cantidad, no quien es el lider)

Existen distintas topologías para comunicarse entre sí, pero como tal no hay formación a seguir.

### Componentes

1. cada partícula cambia su posición $x_i$ a través de 2 factores:

	1. La mejor posición encontrada por sí misma $p_i = p_i1, p_i2, p_iD$ 
	2. La mejor posición encontrada por el enjambre o subconjunto de ella (otra topología) $p_g = p_g1, p_g2, p_gD$

2. 


### Vecindario de Partículas

Se debe definir un vecindario para cada partícula. Este vecindario denota la *componente social* entre partículas.

1. Método *gbest* (mejor global)
2. Método *lbest* (Mejor local)

![[Pasted image 20260514150002.png]]

### Composición

1. Vector $X$ que almacena la *posición* de la particula en el espacio de búsqueda
2. Vector $P$ *mejor solución* encontrada por partícula
3. Vector $V$ *dirección* hacia donde irá la partícula

### Tutorial

En cada iteración, cada partícula realizará las siguientes acciones:

1. Actualización de la velocidad
	Define la cantidad de cambio que se le aplicará a una partícula 
	![[Pasted image 20260514150021.png]]
	- Velocidad = velocidad anterior + Posicion 1 * C (factor cognitivo) * (mejor solucion - posicion anterior) +  Posicion 2 * C (factor social) * (mejor solucion grupal - posicion anterior)
	- $C1$ y $C2$ los pondero yo
	![[Pasted image 20260514150215.png]]
	- Le agrego un factor de inercia $w$ para ponderar la velocidad anterior (por eso se ve más pequeño la velocidad)
2. Actualización de la posición
	Cada partícula actualiza su posición en el espacio de búsqueda
	$$x_i(t) = x_i (t-1) +  v_i(t)$$
3. Actualización de lo mejor encontrado por las partículas
	Cada partícula realizará las sgtes actualizaciones:
	![[Pasted image 20260514150847.png]]	

### Pseudocódigo

![[Pasted image 20260514151144.png]]


# Clase 13
18/05/26

## Ant Colony Optimization

Algoritmo de colonia de hormigas -> Población de soluciones.

### Modelamiento de feromonas

Donde haya menos feromonas hay mayor castigo que el camino donde haya mas feromonas


- $\Delta$ 32
	- 1 / $L_K$ si la hormiga viaja desde $i$ hasta $j$
	- 0 para otro caso
- Sin evaporación
- Con evaporación ($p$ $E [0,1]$ )

cuando uno tiene evaporacion es más fácil de exploración. Pueden tomar caminos malos que como se van a evaporar pueden tomar otros caminos para tener *mayor control de exploración*


La forma de dejar feromonas en el camino es 
-> 1 / costo de tomar el camino


![[Pasted image 20260518150627.png]]

Sin evaporación = 1/14 + 1/31
Con evaporación = (1-p) * 3 + (1/14 + 1/31)

- 3 es la feromona que ya estaba antes 
- si quiero castigar la feromona pongo $p = 0$ 

Lo ideal es usar con evaporación para problemas reales de gran tamaño


### Cálculo de las Probabilidades
¿Cómo yo le asigno la probabilidad de que una hormiga tome un camino?

-> Tanto por la matriz de costo por la matriz de feromonas

![[Pasted image 20260518145945.png]]

$L_{imj}$ = Costo del camino
$P_{i,j}$ = Probabilidad de cada camino = (Matriz de feromonas)^ * (Costo del camino)
					Dividido por:   Sumatoria de lo mismo pero total (todos los caminos)

$\alpha, \beta$ =  parámetros 

-> Al final es *estocástico (aleatorio)* 
La idea es que exploren por lo que no me interesan que vayan por solo un camino


# PAPER
26/05/26

## Binary Bat Algorithm

El codigo original BA está hecho para problemas continuos. Sin embargo, se propone más adelante una version para problemas discretos (números binarios).

### Bat Algorithm

Los murcielagos estan compuestos por (vectores):
- Posición $X_i$
- velocidad $V_i$
- frecuencia $F_i$

Parámetros como Pulses rates $r_i$, y loudness $A_i$

Los murciélagos tienden a disminuir la potencia $A_i$ e incrementar el ratio del sonido ultrasonico emitido cuando cazan.

$Gbest$ es un numero random de distribucion uniforme entre [0,1] usado para tener diversidad y tener la mejor solucion y garantizar *exploracion*.

- Los murciélagos van comparando soluciones con $Gbest$ para ir mejorando la solución global ajustando frecuencia, actualizando velocidades y posiciones

- (Si rand > $r_i$)
	Selecciona una solucion entre las mejores soluciones aleatoriamente. Genera una solucion local alrededor de las mejores soluciones.

$\epsilon$  es un numero random entre [-1, 1] 
$A$ es el loudness/potencia del sonido emitido para mejorar exploracion en vez de explotacion.

Se usan también constantes $\alpha$ y $\gamma$ como valores de enfriamiento.
	Se actualizan cuando se encuentra una nueva solución para garantizar que el murcielago encuentre la mejor solucion


### Binary Bat Algorithm

Un espacio binario puede ser considerado como hipercubo. Las partículas pueden navegar sólo en las aristas del hipercubo.

El problema radica en cómo traducir la velocidad continua en valores que van de 0 a 1. 

La idea es cambiar la posición de la partícula/agente con la probabilidad de velocidad:

- Una función de transferencia es necesario para mapear valores de velocidad y actualizar la posicion con probabilidades.
- Básicamente: Define la probabilidad de cambiar la posicion del vector de 0 a 1 y viceversa.

- El rango de la función de transferencia debe intercalar entre [0,1] como representación de la probabilidad de que la particula debe cambiar su posición.

La gracia de la función de transferencia en forma de V es que es una gráfica periódica, es decir: la función sigmoide original llega a un punto donde si sigo aumentando la velocidad siempre será 0, en cambio con v-shaped propuesto, aunque haya una disminución mínima de velocidad puede caer entre [0,1] porque va repitiéndose la función periódicamente.

En resumen:
1. Se toma el vector de velocidad $V_i$ para usar la función de transferencia
2. El vector de posición se toma como tal y se combina con el nuevo vector de velocidad, combinándose en una ecuación con un valor $Rand$ que va entre $[0,1]$.
3. Se usa la ecuación (10) para la nueva posición $$
   x_i^k(t+1) = 
\begin{cases} 
(x_i^k(t))^{-1} & \text{If } \text{rand} < V(v_i^k(t+1)) \\ 
x_i^k(t) & \text{rand} \geq V(v_i^k(t+1)) 
\end{cases}
   $$
4. Si se actualiza (1), si no (0) la nueva posición del vector en un *espacio discreto*


# Clase 14
28/05/26

## Optimización Multi-Objetivo

En la realidad uno puede tener más de un objetivo -> La forma de proceder es la misma

- Puedo tener muchas soluciones buenas

EJ) Ferrari  puedo tener 2 objetivos
- Disminuir el tiempo para alcanzar 100 km/h
- Maximizar la autonomia del vehiculo

El punto es que ahora tengo soluciones como ejes en una gráfica 

![[Pasted image 20260528150934.png]]

Hay 2 soluciones que no se dominan entre si porque son mejores en su propio ambito 
-> Varias soluciones que son buenas
### Frontera de Pareto

![[Pasted image 20260528151143.png]]

Todas esas soluciones son igual de buenas que el resto que aparecen en la linea.
La idea es mejorar la frontera.

Casi todo es con PSO o genético, poco explorado a través de árboles.

- Las soluciones que son malas me dan diversidad para mejorar la frontera a largo plazo.

## NSGA ll (Non-Dominated Sorting Genetic Algorithm)




# Clase 15 
01/06/26

## Multi-Objetivo Pt.2

Supongamos que tenemos 2 funciones objetivo para $min \space f_1(x), f_2(x)$
Cada función tiene un dominio en particular.

- Cada solución del espacio tiene su f.o. 1 y f.o. 2

### Frontera / Optimalidad de Pareto
! Pareto es la frontera

Es cuando yo tengo una solucion factible si retorna un valor mejor en alguna de sus f.o y *no empeora ninguna de las otras soluciones*.

Cuando ya no las puedo mejorar más es un *Pareto óptima*
- No garantiza encontrarla porque es muy caro computacionalmente

**Soluciones dominadas** -> SI es peor o igual en cada una de las componentes de la F.O

Si encuentro una mejor frontera, NO elimino las otras para proporcionar mayor diversidad.

## Optimización Evolutiva

Los algoritmos evolutivos funcionan bien para resolver problemas de optimización multi-objetivo, ya que pueden trabajar 

1. Non-Dominated sorting genetic algorithm (NSGA-II)


**Tutorial**
1. Ordeno las fronteras según que tan buenas son
2. COmparo los rankings de frentes no dominados
	

![[Pasted image 20260601150144.png]]


### Comparación de Rankings de frentes no dominados

Dado dos soluciones $i$ y $j$, la solución $i$ es preferida por sobre la solución j si $R_i < R_j$
- Cuando dos soluciones pertenezcan al mismo frente. preferimos aquella que se encuentre en la zona menos poblada por *diversidad* (hacia abajo)
- Esta métrica se llama *Crowding distance* -> Calcula 

¿Cómo se calcula?

1. Ordeno las soluciones i de una frontera en orden ascendente de $f_m$ y calcular:
![[Pasted image 20260601151223.png]]
2. Repetir el paso anterior para cada objetivo y encontrar la distancia crowding de la solucion i
	![[Pasted image 20260601151236.png]]
3. Cada dos soluciones, se "hace torneo para elegir i sobre la j si" Rr < Rj o Ri = Rj
![[Pasted image 20260601151317.png]]



### Generación de la población

Existen los operadores de cruzamineto y mutación

- Para la selección de individuos se utiliza torneo. El ganador se define asi:
	- Gana el de mejor ranking (frente)
	- En caso de empate, se decide por crowding distance

### Resumen

1. Generar una poblacion aleatoria P
2. Ordenar por frente y calcular distancia crowding de cada individuo en P
3. Generar una nueva población Q
4. Re-ordenar
	 Población actual P
	 Población generada Q
	- Ordenamiento No dominado (por función objetivo) para la nueva generación.


# Clase Francesa
08/06/26

Gilles Trombettoni
## Interval Methods and Applications

La clave es cómo reducir el dominio del problema para ser eficiente, sin perder soluciones.

- Aproximaciones de valores no representables para computador
- Para reales aplicaciones reducimos valores continuos a aproximaciones.

El  proposito principal:
- Sistema de ecuaciones 
- Global optimizacion
- Estimacion de parametros
- Sistemas dinámicos (robots)

¿Qué es un intervalo? -> Conjunto de valores
¿Qué es una caja? -> Conjunto de intervalos

Cualquier operación que se haga no puede salirse de los márgenes de los números Ireales (para valores computacionales).

EJ) Queremos encontrar la intersección entre 2 círculos, y quiero encontrar todas las soluciones dentro de la caja. ¿Cómo reduzco el dominio?

1. Evalúo toda la caja con los dominios de cada función si pertenece al intervalo
2. Si elijo cualquier valor dentro de la caja, la imagen del primer círculo debe ser 0

Tenemos que probar que no exista ninguna solución dentro de la caja para poder descartarla

Pero podemos mejorar aún más las funciones para reducir más el dominio de búsqueda. No es un exacto el resultado que obtenemos, siempre una aproximación, estos se llaman **Inclusion Functions**

Less accurance -> More aproximate

-> Derivar 

Dado que es derivada, en el caso de ejemplo está entre [4, 31]
Dado que son > 0 , la función siempre crece y por lo tanto puedo obtener el óptimo global con respecto a la función sin derivar.

- Monotonic Inclusion Function
Reemplazo el intervalo de x por un punto en concreto para obtener intervalos, miminizando y maximizando el intervalo final

### Contraction
Reducir el dominio o la caja sin excluir ninguna válida solucion.

EJ) Gráfica de 2 funciones (azul y rojo) cruzando 2 veces.

1. Reduzco el dominio donde recorre la función más pequeña
2. Reduzco nuevamente a la función más pequeña
3. Me detengo cuando ya no puedo reducir más por posibles soluciones por funciones completas
4. Reduzco ahora por constrains (donde sé que $f_1$ no colisiona con $f_2$)
5. Ahora hago busqueda combinatoria
6. Hago lo mismo para ambos lados
7. Sigo reduciendo el espacio hasta encontrar el punto donde puedo colisionar

Sabiendo la respuesta que busco, con este metodo busco los valores que me dan este resultado

### Interval Branch & Bround
El problema de la optimización global




















