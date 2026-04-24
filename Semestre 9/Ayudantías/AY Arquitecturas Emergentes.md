# Ayudantía 1
25/03/26

1. Arquitectura
2. Modelo 4+1
3. Diferentes tipos de arquitectura
4. Temas emergentes

## 1. Arquitectura
Diseñar un sistema e implementar todas las apis para un buen funcionamiento

Controla como interactuan los subsistemas entre si, bajo que reglas interactúan y es en esta etapa donde se toman decisiones de diseño.

## 2. Modelo 4+1
Diseñado por Philippe Kruchten. Te dice como diseñar un sistema lo más limpio posible para que el sistema entienda.

1. Vista logica
2. Vista de despliegue
3. Vista de procesos
4. Vista física
5. Vista observador

### Vista lógica
Describe las funciones y estructura lógica del software. Muestra módulos o clases y sus interacciones principales. No necesito ser un crack para saber lo que necesita el sistema.

Diagramas: Clases, componentes, comunicación

### Vista de Desarrollo / Despliegue
Perspectiva del desarrollador sobre la organización del código (lo más programable posible)
- Agrupa módulos, paquetes y componentes implementables

Diagramas: Componentes, paquetes

### Vista de procesos (Dinámica)
Vista más escalable y rendimiento
- Más sistema distribuidos

### Vista Física (Casos de uso)
Lo que se usa en empresas, ver qué hardware se usará (como servidores a usar)
- Distribución física de componentes

Diagramas: Despliegue (servidores y redes)

### Vista de Escenarios +1
Integra y valida todas las vistas anteriores
- Usa casos de uso o escenarios para verificar la arquitectura

Diagramas: Secuencia de interacción, flujos de casos de uso

## 3. Arquitecturas tradicionales

### Monolítica
Para 1 usuario o un sistema

- [p] Desarrolo y despliegue simple
- [p] Rendimiento interno bueno
- [c] Escalabilidad limitada (escalado conjunto)
- [c] Mantenimiento difícil a medida que crece 

### Cliente/Servidor (2 capas)
Como usuario tengo una app web donde me conecto directamente al servidor

Cliente: Interfaz de usuario (frontend)
Servidor: Maneja datos y lógica central

### N-Capas o 3 capas
Siempre empieza desde el cliente hacia abajo (iceberg)

1. Presentación UI
2. Lógica de Negocio: Procesos y reglas del negocio
3. Datos: Servidor de bases de datos

- [p] Mayor modularidad y flexibilidad
- [p] Facilita cambios aislados en cada capa sin afectar las otras

EJ) API -> API -> KAFKA-> SQL

## 4. Arquitecturas Cloud
Lo mas choro actualmente para aprovechar la elasticidad y escalabilidad que ofrecen los proveedores como aws o google cloud

[Cloud-Native] Trabajo con servicios open source tipo cloude
[Microservicios] Se divide en multiples servicios independientes

- [p] Escalabilidad independiente
- [p] Desarrollo y despliegue autónomo de cada servicio, favoreciendo la agilidad

**DESAFIO**: Mayor complejidad en la integracion, gestion de comunicaciones, descubrimiento y seguridad entre servicios

> Bucket se almacenan documentos 

[DIseño modular] Separar por funciones independientes para evitar leseos
[Contenedores y Orquestación] Se usan contenedores (docker) para gestionar el despliegue, escalado y resiliencia de estos contenedores
[Automatización y Agilidad] Se automatizan procesos para el despliegue continuo, la integración y la recuperación ante fallos, permitiendo responder rápidamente a cambios en la demanda
[Infraestructura Elástica] Tiene que estar todo listo para poder escalar horinzontalmente rápidamente


# Ayudantía 2
01/04/26

Nicolas.ramirez_a@mail.udp.cl

1. Cloud computing
2. Modelos de servicio Cloud
3. Ejemplos de arquitecturas cloud
4. Temas emergentes

## Cloud Computing

Modelo que permite el acceso bajo demanda a recursos de computación a través de Internet
- Servidores, almacenamiento, bases de datos y software

EJ) Google drive, gmail, netflix, Spotify

## Características de la Nube

- *Autoservicio bajo demanda* 
	No necesita intervención directa
- *Elasticidad*
	Se puede escalar automáticamente la capacidad, hacia arriba (más potencia) o hacia los lados (más nodos)
- *Pago por uso*
- *Acceso Constante*
	Acceso desde cualquier lugar con conexión a internet
	*DNS*: Si tu pones www.google.cl te envía a distintos ips a través del país, tiene sus propios servidores DNS para redireccionar a servidores con menor uso por ej.
- *Multi - Tenacy*
	Múltiples usuarios comparten la misma infraestructura de forma aislada y segura

## Sistemas de Arquitectura

### IaaS - Infraestructura como Servicio

Ofrece infraestructura de IT básica a través de internet como servidores, almacenamiento, redes y sistemas operativos.

*Ventaja principal*: Tienes control total del entorno, como si fuera tu propio servidor físico, pero  sin tener que mantenerlo

EJ)
- AWS EC2
- Microsoft Azure (VMs), Google
- Compute Engine

No tengo que estar pagando la licencia 
Problema -> Tengo que instalarlo desde otro país, necesito a alguien que esté encargado de la instalación de infraestructura 

- [p]  Sistema a ocupar mucho porque cuando hagamos pruebas es más barato contratar IaaS

### PaaS - Plataforma como Servicio

Mucho más complejo. Ya viene todo instalado, falta agregar el código deseado.
Ofrece entorno listo para usar donde puedes desarrollar, probar y desplegar aplicaciones, sin preocuparte por la infraestructura subyacente.

*Ventaja principal*: Permite desarrollar más rápido, con menos tareas de mantenimiento  técnico

No tienes control sobre la base y entorno a ocupar. Ya te dan toda la infraestructura lista, solo tienes que llegar y programar por asi decirlo

EJ)
- Google App Engine
- Microsoft Azure (VMs)
- Google Compute Engine

### SaaS - Software como Servicio

Ofrece la app ya lista para usar como app o por navegador, sin necesidad de instalar nada ni gestionar infraestructura.

*Ventaja principal*: Accedes al software desde cualquier lugar, sin preocuparte por instalaciones o actualizaciones.

Usado por empresas que no tienen áreas de informática, porque buscan módulos ya hechos para usar con 1 click

EJ)
- SAP
- Gmail
- Microsoft 365
- Zoom

## Arquitecturas Híbridas y Multinube

### Arquitectura Híbrida
Combina infraestructura local *(on-premise)* con servicios en la nube pública. Ideal para empresas que migran gradualmente o que manejan datos sensibles localmente.

EJ) Gobierno de chile

### Arquitectura Multinube
Usa múltiples proveedores cloud (ej. AWS + Azure) al mismo tiempo.
Busca evitar dependencia de un solo proveedor *("vendor lock-in")*.

-> Más usado, por ej retails
-> tienes que tener 1 ingeniero para cada una de las nubes
-> En el caso de que se caiga una, usar la otra nube

## Microservicios y Contenedores

Divide una app en servicios pequeños e independientes, donde cada uno cumple una función específica dentro del sistema.

Estos se comunican entre sí mediante interfaces API, como REST o gRPC y pueden ser desplegados, escalados y actualizados de forma individual, lo que otorga mayor flexibilidad, modularidad y resiliencia al sistema en comparación con arquitecturas monolíticas

*Microservicio*
Si yo tengo un microservicio, lo corro en un instancia donde ya esta todo listo

Una arquitectura de microservicios divide una app en servicios pequeños, independientes y especializados

*Contenedor*
Tengo que crear la instancia, sistema, software, todo en general haciendolo más pesado en general

Los contenedores empaquetan una aplicación junto con todas sus dependencias, asegurando su ejecución consistente

-> Los microservicios suelen desplegarse dentro de contenedores

## Serverless y FaaS (Functions as a Service)

APIS pre-desarrollado. Tienen todo ya predispuesto, el desarrollador no necesita gestionar servidores. Solo escribe el código y el proveedor cloud se encarga de todos los demás: aprovisionamiento, escalado, mantenimiento, etc.

*Ventajas*
- Sin gestión de infraestructura: el proveedor maneja los servidores por ti
- Escalado automático: Las funciones se escalan según la demanda, incluso a millones de ejecuciones
- Pago por ejecución: solo pagas por el tiempo real en que tu código se ejecuta
- Rápido despliegue: solo necesitas subir la función, sin preocuparte por el entorno


## Arquitectura Big Data

Sistema y gestación de datos a gran escala

* Ingesta de datos (Streaming o batch)
	- Servicios como Apache Kafka (sincronización), Google Pub/Sub, AWS kinesis
	- Reciben datos desde sensores, apps, logs, clics de usuarios, etc
- Procesamiento de datos
	- En lote: Apache Spark, Dataproc, Twitch
	- En tiempo real: Apache Flink, Google Dataflow, AWS Lambda
- Almacenamiento Escalable
	- Data lakes: Amazon S3
	- Bases de datos: BigQuery, Redshift, Snowflake
- Análisis y visualización
	- Herramientas: Google Data Studio, Power Bi, Looker
	- Machine Learning: Vertex AI, SageMaker (AWS), Databricks (Azure)

*Ventajas*
- [p] Escalabilidad prácticamente infinita
- [p] Pago por uso
- [p] Alta disponibilidad y redundancia
- [p] Integración con IA y servicios avanzados


# Ayudantía 3
08/04/26

## Cloud pepe

### ¿Dónde desplegar?

- On-Premise -> en tu empresa
- Data center externo
- Cloud provider (AWS, Google cloud, Azure)

### Elección de Región !!

1. Conformidad legal
2. Disponibilidad
3. Latencia
4. Precio

> Elegir mal la región puede afectar rendimiento, costo y cumplimiento legal.
### Regiones y Zonas de Disponibilidad !!

Región -> Conjunto de zonas
Zona -> Centro de datos

## Modelo de Responsabilidad Compartida

Ordenado qué tanto soy responsable yo, desde totalmente responsable a casi nada de desponsabilidad mia.

1. On-Premises: Lo hago todo yo
2. IaaS
3. PaaS: 
4. SaaS: SAP
5. FaaS: Funcionalidad (gmail)

Siempre sera clasificación y contabilidad de datos los que manejo yo, no la empresa externa.


![[Pasted image 20260422103539.png]]


## IAM - Gestión de Accesos
IAM controla quién puede acceder a qué.

- Usuarios
- Grupos
- Políticas

Genera grupos que pueden llamarse x, generando politicas de acceso

## Cómputo - EC2
Es como arrendar un computador en la nube

- Máquinas virtuales
- Configuración: CPU, RAM, red

![[Pasted image 20260422103448.png]]

## Ciclo de Vida de instancias

*Estados*:
- Pendiente: Cuando estan iniciando y prueban si funciona o no
- Ejecutándose: 
- Detenida !!: Mantenimiento y soporte (hace perder dinero)
- Terminada

1. Planificación Inicial
2. Análisis detallado
3. Diseño estructural
4. Desarrollo principal
5. Integración de pruebas
6. Implementación práctica
7.  Mantenimiento y Soporte

![[Pasted image 20260422103659.png]]

## Almacenamiento
Existen 3 tipos

1. Bloque (EBS)
	- Disco duro
	- Persistente
2. Objeto (S3) 
	- Archivos
	- Escalable
3. Archivo
	- Similar a carpetas


# Ayudantía 4 - Solemne 1
15/04/2 6

## Pregunta 1
Arquitectura en Capas

Piden: Arquitectura Seguro, escalable y disponible 24/7

- Diseñar solución usando el modelo 4+1

a. Presente la vista lógica con entidades, atributos y relaciones clave








