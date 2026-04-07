# Definiciones 

### Ingeniería de Software
Es la disciplina completa. Abarca todo el ciclo de vida: desde la captura de requisitos, gestión de equipos, aseguramiento de calidad (QA), testing, procesos (Scrum/Kanban), hasta el despliegue y mantenimiento. Se enfoca en la eficiencia del proceso de creación.

### Arquitectura de Software
Se enfoca en las decisiones de diseño que son difíciles de cambiar. No le importa cómo se gestiona el equipo, sino cómo se dividen las responsabilidades del sistema (módulos) y cómo interactúan para garantizar atributos como la escalabilidad o la seguridad. Cada decisión genera costos de diseño y arquitectura, riesgos.

# Requerimientos No Funcionales
Atributos de calidad

- *Performance*: Respuesta eficiente, pocos componentes, operaciones criticas concentradas
- *Escalabilidad*: Aceptar mayor carga sin degradación, crecimiento horizontal
- *Mantenibilidad*: Soportar nuevos requisitos
- *Seguridad*: Proteger acceso y datos
- *Confiabilidad*: Sistema siempre activo
	- Componentes redundantes
	- Fácil migración
	- Bajo acoplamiento
	- Control distribuido
	- Activo-Activo o Activo-Pasivo
- *Integrabilidad*: integración con otros sistemas y apis
- *Portabilidad*: Independencia de plataforma (dockers o VM)
- *Verificabilidad*: Capacidad de autotesteo en tiempo real
- *Soportabilidad*: Manejo de errores, diagnostico y corrección de incidencias

# Estructuración - Arquitecturas

0. Analizar el contexto
1. Estructuración
2. Modelo de Control
3. Descomposición modular: Diseño de cada componente

## Cliente/Servidor
El más simple, el cliente pide datos directamente al servidor. Puede ser multicliente

- [p] Centralización de datos, fácil de mantener
- [c] Punto único de falla si no se instancian. Cada server es independiente y no comparten datos

EJ) un sistema de cajero automático. El cajero es el cliente que pide el saldo, y el servidor central del banco responde

![[Pasted image 20260406223748.png]]
## Arq Orientada a Servicios - SOA
Evolución del cliente/servidor (bus de servicio)

- [p] Comparte servicios, reutiliza, escalable y mantenible
- [c] Bus único punto de falla. Complejidad

EJ) El sistema interno de una aerolínea. El servicio de reserva que se comunica con el de pagos y el de milla-pasajero, que pueden estar en tecnologías distintas.

![[Pasted image 20260406223738.png]]

## Micro-Servicios
Se expande tanto que son distintos servicios completamente independientes que hacen una sola cosa muy bien. Cada uno tiene su propia base de datos.

- [p] Escalabilidad e independencia de servicios
- [c] Altísima complejidad de monitoreo y comunicación

EJ) Netflix. Un micro-servicio se encarga de portadas, otro de recomendaciones, otro de video, etc... 

![[Pasted image 20260406224011.png]]

## Modelo de Capas
Se puede usar como forma de organizar en secuencia y niveles de abstracción. Describe más la estructura interna del código de forma complementaria. Permite desarrollo independiente de cada capa

- [p] Modificable fácilmente
- [c] Puede ser lenta (performance) al ir capa por capa

EJ) Una aplicación de escritorio contable. Separa la pantalla donde ingresas números. de las reglas de impuestos y de la base de datos local.

![[Pasted image 20260406224124.png]]

## Modelo de Repositorios
Útil cuando muchas aplicaciones deben compartir grandes volúmenes de datos. Gestión centralizada o distribuida de almacenamiento.

Existen dos tipos de modelos:
*Pasivo*: Las aplicaciones leen/escriben directamente
**Proactivo**: El repositorio notifica cambios a las aplicaciones

- [p] Separa lógica de negocio de acceso a datos
- [p] Eficiente de compartir datos
- [c] Difícil cambio de modelo de datos
- [c] Posible único punto de falla

![[Pasted image 20260406224520.png]]




## Objetos Distribuidos
Cada componente (objeto) define sus datos y métodos. Comunicación a través de un ORB (Object Request Broker). 

Muy compleja pero muy flexible
- [p] Muy flexible, escalable y mantenible
- [c] Compleja construcción, bajo rendimiento

![[Pasted image 20260406224730.png]]


## Cloud
Externalización de servicios bajo modelo de pago por uso (recursos elásticos)

![[Pasted image 20260406224852.png]]

- [p] Servicios ubicuos, reducción de costos
- [p] Disponibilidad, escalabilidad, flexibilidad, movilidad y elasticidad
- [c] Dependencia de servicio externo
- [c] Riesgos de seguridad y dependencia de conectividad


## Comparativa

![[Pasted image 20260406230552.png]]

# Arquitecturas Genéricas: Modelos de Control
Define cómo se gestiona el flujo de ejecución entre componentes. 

## Control Centralizado

### Modelo Call-Return
Un componente controla la ejecución llamando a otros en secuencia. Cada llamada espera una respuesta antes de continuar

- [p] Simple y predecible
- [p] Testeable con facilidad
- [c] Rídigo, Bloqueante
- [c] Complejo manejo de excepciones

### Modelo Manager (Admin)
Componente central coordina la ejecución de otros procesos (útil ensistemas concurrentes)

- [p] No bloqueante
- [p] Coordinación de procesos paralelos
- [p] Lógica centrada en administrador
- [c] Posible cuello de botella

## Control Basado en Eventos
Los componentes responden a eventos generados externamente. No bloqueante por naturaleza

### Broadcast
Los componentes publican servicios, gatillan eventos y suscriben a eventos de otros. LA activación es descentralizada.

- [p] Activación descentralizada, Evolución simple del sistema
- [c] No garantiza orden, Varios manejadores pueden responder al mismo evento

### Manejo de Interrupciones
Usado en sistemas en tiempo real. Cada tipo de interrupción tiene su propio manejador que responde inmediatamente sin bloqueo y con capacidad de procesamiento paralelo.

## Comparativa

![[Pasted image 20260406230519.png]]


# Ejercicios Control 1


1. “Tal como su nombre lo sugiere, la arquitectura Cliente / Servidor está estructurada por componentes cliente y componentes servidor. El cliente es el encargado de recibir los requerimientos del usuario y redirigirlos hacia su correspondiente proceso servidor. Esto implica que cada cliente debe tener una contraparte que sea servidor, dado que ambos, en conjunto, deben satisfacer un requerimiento del usuario.”

R: FAKE: no necesariamente por cada cliente debe haber una contraparte como servidor

