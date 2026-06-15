
## 2025

1. ¿Cuáles son los métodos usados para la selección de individuos en los algoritmos genéticos? Describir cada metodo, ventaja y desventaja de cada uno

- Ruleta
	La ruleta escoge aleatoriamente un individuo estrictamente proporcional a su valor de fitness, es decir, mientras mayor sea el valor de fitness, mayor es la probabilidad de ser escogido por la ruleta.
	- Ventaja -> Facilita que el cruzamiento se de entre los individuos con mejor fitness aleatoriamente
	- Desventaja -> Individuos con un fitness altisimo puede abarcar toda la ruleta, siendo un fuerte sesgo inicial que pierde la diversidad poblacional y llega a una convergencia prematura del algoritmo.
- Torneo
	De N individuos, elijo $k$ individuos aleatoriamente y de ellos escojo al individuo con mejor fitness. Si necesito $T$ individuos, realizo $T$ torneos.
	- Ventaja -> Computacionalmente muy eficiente, porque no requiere calcular el fitness total de la población ni ordenarla (como la ruleta)
	- Desventaja -> Existe el riesgo de que nunca se enfrenten las mejores soluciones, produciendo pérdida de datos 

2. Explique el efecto que tiene la tasa de evaporación en el algoritmo de colonia de hormigas (ACO). Además, entregue una recomencación (con justificacion) de cómo usar dicho parámetro

	La evaporación funciona tanto para exploración como explotación. Al empezar, las hormigas recorren todos los caminos, dejando feromonas, por lo que el camino que sea más corto se recorrerá más veces porque es donde hay más feromonas. Si hay evaporación, los otros caminos evaporarán y las hormigas recorrerán el camino con más feromonas. En cambio si no hay evaporación, las feromonas se acumulan e irán siempre por el mismo camino, favoreciendo la explotación.

	Para problemas reales, se recomienda un valor intermedio, en torno a $p = 0,5$, castigando la mitad de feromonas y manteniendo el resto sumando las nuevas para mantener un mejor control de exploración.


3. ¿Cuál es la utilidad de usar topologías para las partículas en el algoritmo PSO? Ejemplifique con dos topologías.

	Su utilidad es establecer el componente social de cada partícula. Sirve para que las partículas compartan información y busquen soluciones en conjunto.
	Dependiendo de la topología, se elige a un lider *gbest* para todo el enjambre o *lbest* para un entorno local
	- Grafo completo y anillo

4. Explique la importancia de la distancia crowding (CD) en los algoritmos evolutivos, usados para la resolución de problemas multiobjetivo

	- Sirve para encontrar la solución más cercana a una posible frontera que mejore las soluciones actuales.
	- Mantiene la diversidad en la frontera de paleto. Sirve para desempatar entre dos soluciones que pertenecen a la misma frontera.
	- El algoritmo escoge los puntos que se encuentran en zonas menos pobladas del espacio para equilibrar las mejores soluciones globales en la frontera.



##### Posibles preguntas

- Estigmergia en el comportamiento de las hormigas en AC
	Se refiere a la cooperación indirecta que ocurre entre las hormigas a través del entorno. Por ej, feromonas que sirve de guía para el resto de la colonia.



## 2024

1. ¿En qué consiste el elitismo en los algoritmos genéticos? ¿Favorecen la exploración o la explotación? Explique.

	Consiste en una estrategia de reemplazo, donde un porcentaje de la población (los mejores) se mantienen y sobreviven para la siguiente generación.

	Favorece la explotación, dado que al concentrarse únicamente en los mejores individuos, el algoritmo se centra en esas soluciones pero pierde diversidad de información en la población.

2. Explique brevemente todas las componentes del algoritmo PSO.

	- Posicion actual
	- Velocidad
	- Mejor solucion propia
	- Mejor solucion del vecindario

3. Explique cómo el algoritmo ACO (hormigas) puede escapar de óptimos locales.

	El uso de evaporación de las feromonas para las hormigas favorece la exploración y escape de óptimos locales, ya que, al tener un factor de evaporación, los caminos desaparecen y "obligan" a las hormigas a explorar nuevos caminos, y el que tenga mejor resultado es el que tenga mayor cantidad de feromonas. Evita también que se acumulen feromonas en un único camino.


4. Suponga que el profe desea resolver una instancia de un problema de optimización NP-Hard, con m restricciones, en donde el número de soluciones factibles es comparable al 2% del tamaño del espacio de búsqueda. Suponga que el profe quiere usar un algoritmo evolutivo ¿Qué recomendación le daría al profesor con respecto a la función de fitness en este caso?

	Dado que el número de soluciones factibles es muy pequeño y muy poco dispersas en el espacio, priorizo explotación. Para esto, la función de fitness debe ser más compleja e incorporar penalizaciones frente a las restricciones del problema
	De esta forma, el algoritmo puede trabajar con las abundantes soluciones infactibles para penalizarlas según la cantidad de restricciones que contradiga.



## Posibles preguntas P1


1. ¿Cuál es la principal diferencia en cómo funciona el operador de cruzamiento en un Algoritmo Genético (GA) clásico versus en _Differential Evolution_ (DE)? Además, ¿para qué tipo de problemas está diseñado DE?

	La principal diferencia es que GA el cruzamiento cambia genes binarios o discretos entre los cromosomas de los padres.
	DE, los genes son números de punto flotante, haciendo una combinacion lineal de las variables seleccionados al azar. Por eso se le considera exclusivo para *dominios continuos*


2. Para PSO, en la ecuación de actualización de la velocidad de una partícula, interviene un peso o factor de inercia (w). ¿Cuál es el objetivo de este factor y cómo afecta la búsqueda si le asignamos un valor muy grande o un valor muy pequeño?

	El objetivo de ese factor de inercia es para ponderar el factor de velocidad. Esto me sirve para controlar qué tanto me afecta en cambiar el rumbo de la partícula al calcular una posible mejor solución.
	Si se le asignan valores grandes favorece la exploración (para pasos más largos)
	Si tiene valores bajos, a la explotación (pasos más cortos)


3. La decisión de qué camino tomará una hormiga es de carácter estocástico y su cálculo de probabilidad depende fundamentalmente de dos matrices de información. ¿Cuáles son estas dos matrices y qué representa cada una?

	Esta depende de las feromonas y el costo que tiene cada ruta para ir a cierto camino.
	Una hormiga preferirá el camino que contenga la mayor cantidad de feromonas, favoreciendo a recorrer el camino con la mayor probabilidad de que sea la solución. En cambio el costo es el que determina si me conviene recorrer cierto camino o no para llegar a la solución


4. En el contexto de problemas con múltiples objetivos, defina con precisión en qué condiciones una solución "domina" a otra (mejora de Pareto). A partir de esto, ¿qué característica principal tienen las soluciones que logran formar la "Frontera de Pareto"?

	Dado que existen múltiples objetivos, una solución dominara a la otra si en ambos objetivos es mejor que la otra. Las soluciones que conforman la frontera de pareto son todas igual de eficientes y buenas opciones a escoger, conformando soluciones no dominadas, donde el criterio final para la solución normalmente termina siendo del humano, dependiendo de lo que se busque.


5. ¿En qué se diferencian los Algoritmos de Coevolución Cooperativa de las estrategias evolutivas clásicas y para qué tipo de problemas resultan particularmente útiles?

	La coevolución es una evolución complementada de especies cercanas. Cada población representa una especie en particular.
	Cada especie desarrolla un subcomponente de la solución, luego se integran los resultados en una solución global.

6. PSO - En la ecuación de actualización de velocidad de una partícula, existen dos constantes clave llamadas C1​ y C2​. ¿Qué nombre recibe cada factor y qué tipo de atracción representan en el vuelo de la partícula?

	 Factor cognitivo y Factor social.
	 El factor cognitivo influye en qué tanta importancia le doy al propio exito historico
	 El factor social influye en la atraccion de la particula al exito alcanzado por el vecindario

7. El algoritmo _Scatter Search_ utiliza un componente llamado Conjunto de Referencia (RefSet). ¿Qué tipo de soluciones debe incluir este conjunto y qué familias de algoritmos mezcla _Scatter Search_?

	Scatter Search integra elementos de metaheuristicas poblacionales y de una solución.
	Tras crear y mejorar la población inicial, extraigo un conjunto de referencia de tamaño moderado (de 100, 10 por ejemplo). Mezclo soluciones con muy buen fitness con otros distintos para no perder diversidad y mejorarlas. Las otras 90 soluciones las descarta por lo que es carisimo computacionalmente.

8. Al buscar la Frontera de Pareto óptima en algoritmos como NSGA-II, se busca un equilibrio entre "convergencia" y "diversidad". ¿Qué implica exactamente cada uno de estos conceptos en el resultado gráfico de las soluciones?

	Convergencia se refiere a la frontera específica que en su conjunto, son las mejores soluciones posibles actuales del dominio, o las que más se acercan a la verdadera frontera óptima de Pareto. Diversidad se refiere a que, para yo poder buscar una mejor frontera, requiero de la diversidad de las otras soluciones que son peores para no perder calidad. Es justo para no perder esta diversidad que se emplea CD.


