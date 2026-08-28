
# Clase 2
14/08/26

## Estructura de Artículos

Empezamos entendiendo la estructura de los articulos

En general tenemos lo siguiente:
- Abstract
- Introduction
- Referencias
- Conclusion

Busqueda de papers: https://scholar.google.com/
Busqueda de conferencias: https://portal.core.edu.au/conf-ranks/
#### Abstract 
- Contexto
- Problema
- No mas de 500 problemas (breve)
- Solucion propuesta

Despues se contextualiza ampliamente

#### Referencia
- Estado del arte
- Dar credito
- Referenciar fuente
- Dar aporte a lo que dije -> *Evitar caer en lo subjetivo*

#### A tener en cuenta

- Año -> Entender en que contexto se genera
Por ej: Paper del 2004 puede ser innovador pero actualmente ser obsoleto
Si es antiguo puede haber servido de base para proyectos a futuro

> Si es citado varias veces es porque fue relevante

- Mala práctica citarse a si mismo o tener demasiadas citas
- USENIx -> Buena conferencia -> Todos A o más
	- ICORE Conference Portal -> Buscar A o a lo mas B

- Para Journal
	- Si tengo la mayor cantidad de citas en el propio journal *Sospechoso*


## Actividad en Clase

*Tabu based Cache to Improve Latency and Load Balancing on Prefix Trees*


# Clase 3
21/08/26

### **A realizar**
Elegir paper para realizar 


# Clase 4
25/08/26

## Ambiente de Big Data

¿Cómo sacarle provecho?

- Netflix wants to generate recommendations based on billions of viewing records
- A fintech company wants to detect fraud in real time as transactions occur
- A network of industrial sensors generates every 100 ms
- A university wants to analyze 10 years of academic data from 20,000 students

1. SI es un escenario de big data -> Volumen alto, restricciones de tiempo, datos 
2. SI -> Depende de responder en *tiempo real*
3. Depende -> Restricciones de tiempo, pero falta información (cuantas transacciones requiere)
4. NO -> Se puede hacer con una máquina

> Es big data cuando hay escenarios desafiantes y no se pueda resolver a partir de una sola máquina

Normalmente la complejidad de análisis es multidimensional

#### 3V:
- Alto volumen
- Alta velocidad
- Alta variedad de información
Ahora:
- Veracidad
- Valor

#### Fases típicas
1. Adquisicion
2. Extraccion
3. Integracion
4. Análisis
hasta ahí llega el informático normalmente
5. Interpretación
6. Decisión

#### Desafíos
- Performance
- Escalabilidad
- Calidad de servicio
- Heterogeneidad 
- Flexibilidad
- Privacidad
- Costos

Lo que más demora es en preparar los datos para su uso correcto.

> Siempre hay que curar los datos de la mejor forma y de ahi pensar en el algoritmo

# Clase 5
28/06/26

## Manejo de Recursos / Resource Management

Nace de poder generar reutilizacion de procesos para manejo eficaz de recursos.

- Throughput 
- Capacity
- Robustness

#### Motivación
- Ofline to Online
- Rápida innovación en computación en la nube/cloud
- No hay un solo framework optimo para todas las apps
- Ejecutar cada framework a su dedicado cluster
	- Caro
	- Dificil para datos compartidos

#### Solución
- Ejecutar multiples frameworks en un solo cluster
- Cómo compartir clusters virtuales a través de multiples y no homogeneos frameworks ejecutaddos en VMs containers?

- Particionamiento  estático
¿Es eficiente? -> NO. No tiende a ser homogéneo en el tiempo los datos 

### Apache Mesos
Este es genérico
1. Capacidad de escalar
2. Puede ejecutar simplemente 
3. Hace balanceo de carga, manteniendo consciencia la máxima capacidad que tenga cada cluster


Mejora el uso de recursos de forma dinámica
EJ) Twitter y Airbnb fueron los primeros usuarios

#### Metas
- Alto uso de recursos
- Diversos frameworks con soporte
- Escalabilidad de miles de nodos (~50.000)
- En caso de fails 

#### ¿Qué es lo que hace?
Provee funcionalidades comunes como
- Deteccion de fallas
- Distribucion de tareas
- Monitoreo
- Killing task
- Task starting

También se pueden replicar tareas 

#### Arquitectura

El maestro envia ordenes a sus esclavos/agentes
- Lo ideal es tener multiples maestros para no tener un unico punto de falla

Si bien logra escalabilidad y su capacidad de generalizar los frameworks

**Problema**
- Centralizado (pero le estamos quitando peso al master)
- Pérdida por sacar hadoop scheduler del master es
	- Sincronización -> Efecto de latencia mayor (costo de comunicacion)
	- Al tener localizado los datos y llega otro valor externo, crea conflicto
	- *Planificación subóptima* -> No tiene visión global del problema

#### Otros componentes

Zookeeper
- Servicio de coordinación para mantenimiento de configuración, info, nombres, sincronización y servicios proveedores 
- Usado en varios sistemas distribuidos, entre Mesos, Storm y Kafka

#### Planificación de Recursos
- Los esclavos notifican al master de los recursos libres
- El master notifica que está disponible x recursos
- Cada framework elige qué oferta le conviene
- *PROBLEMA*: Posible retraso de tarea para grandes proyectos

#### Mecanismo de Justicia/Ofertas
Tengo que ofertar en un orden predeterminado, usando **DRF** Dominant Resource Fairness

- La idea es ser justo a la hora de ofrecer recursos}
- Saca la relación porcentual del recurso que estoy ofreciendo, de forma que veo cuál es el dominante


### Resumen

Permite escalar hacia el planificador
Mayor flexibilidad porque cuaquier framework lo puede usar

Contras:
- Costos de despliegues
	- Planificaciones suboptimas 


## Apache YARN

Hadoop dedicado para clusters
La gracia es que puedo implementar planificadores personalizados 

Simplemente se reportan los recursos y estos se planifican a través de un maestro
- Mucho menos flexible que el anterior (que soporten yarn)

Está el Global ResourceManager **RM** que envía paquetes a los Node Manager

RM -> Node Manager -> Container