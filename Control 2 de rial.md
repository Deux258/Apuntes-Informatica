1. ¿Cuáles son los métodos usados para la selección de individuos en los algoritmos genéticos? Describir cada metodo, ventaja y desventaja de cada uno

	1. Ruleta
	La ruleta me conviene para evitar convergencia de soluciones en etapas tempranas, escogiendo al azar individuos para explorar. Puedo modificar las probabilidades a través del fitness, donde el que tenga mayor valor de fitness, mayor es la probabilidad de escoger a ese individuo.
	Ventaja -> Facilita que el cruzamiento se de con los que tienen mejor fitness
	Desventaja -> Debo calcular todos los fitness, además de que los individuos con mayor valor de fitness saldrán la mayor parte del tiempo, por lo que me limita la diversidad.
	*Convergencia prematura*

	2. Torneo
	Puedo escoger mi subconjunto y enfrento a los individuos, ganando el que tenga mayor valor de fitness.
	Ventaja -> Computacionalmente muy eficiente, porque limito el cálculo de fitness para un subconjunto, y si necesito T individuos, empleo T torneos
	Desventaja -> Existe el riesgo de que nunca se enfrenten las mejores soluciones, produciendo pérdida de datos

2. Explique el efecto que tiene la tasa de evaporación en el algoritmo de colonia de hormigas (ACO). Además, entregue una recomencación (con justificacion) de cómo usar dicho parámetro

	A mayor evaporación, ,mayor exploración.
	A menor evaporación, mayor explotación

	Un valor que puede servir para casos reales es 0,5 la tasa de evaporación, para que no haya un exceso de evaporamiento y las hormigas puedan seguir explorando rutas que no sean tan convenientes en un inicio, pero a la larga sea la solución global.

3. ¿Cuál es la utilidad de usar topologías para las partículas en el algoritmo PSO? Ejemplifique con dos topologías.

	La ventaja de usar topologías es que, las partículas se comunican entre sí, agregando un factor social a la ecuación para decidir si se sigue la mejor solución como vecindario o solución como partícula. Ayuda a explorar coordinadamente, usando topologías como anillo o estrella.

4. Explique la importancia de la distancia crowding (CD) en los algoritmos evolutivos, usados para la resolución de problemas multiobjetivo

	Sirve para encontrar la solución que se encuentre más cerca a una posible mejor frontera de paleto.
	Mantiene la diversidad, sirviendo para desempatar cuál vendría siendo la mejor solución que pertenezcan en una misma frontera.
	El algoritmo escoge lugares que estén menos pobladas para ayudar a mejorar la diversidad de soluciones

5. ¿En qué consiste el elitismo en los algoritmos genéticos? ¿Favorecen la exploración o la explotación? Explique.

	Consiste en la selección de un porcentaje de la población (los mejores) en el trascurso de generaciones, se mantienen y sobreviven a la sgte generación
	Favorece a la explotación, dado que se concentra en unos pocos ejemplares (que son los mejores), pero pierde diversidad e información en la población.

6. Explique brevemente todas las componentes del algoritmo PSO.

	- Posicion actual
	- Próxima posición
	- Velocidad
	- Mejor solución como particula individual
	- Mejor solución del vecindad

7. Explique cómo el algoritmo ACO (hormigas) puede escapar de óptimos locales.

	

8. Suponga que el profe desea resolver una instancia de un problema de optimización NP-Hard, con m restricciones, en donde el número de soluciones factibles es comparable al 2% del tamaño del espacio de búsqueda. Suponga que el profe quiere usar un algoritmo evolutivo ¿Qué recomendación le daría al profesor con respecto a la función de fitness en este caso?

	Le recomendaría un valor alto de fitness, dado que al haber muy pocas soluciones factibles en un dominio reducido, me conviene ir por explotación de soluciones y para esto, un valor de fitness alto con penalizaciones me conviene para castigar aquellas soluciones que no cumplan con las restricciones.

