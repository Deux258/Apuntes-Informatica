	
## Ejercicios

### Identificar Riesgos

1.- “Falta de capacitación del equipo en la nueva arquitectura cloud.”

R: Alta probabilidad de desarrollar mal o ejecutar incorrectamente algún componente, además de atrasos para capacitar al equipo. Posibles manejos erroneos del cronograma, 
- Alcance
- Riesgos

2.- “Que el proyecto de migración de datos sobrepase el presupuesto.”

R: El mayor riesgo aquí es la limitante del presupuesto, tanto para pagar los recursos, como para pagar a los trabajadores. Por ejemplo, limitante de espacio y se requiere comprar discos duros.


3.- “Debido al retraso en la aprobación de requerimientos por parte del cliente, el módulo de facturación podría no completarse a tiempo”

4.- “Debido a la entrada en vigencia de la nueva Ley de Protección de Datos, el sistema debe incorporar un módulo de encriptación de datos, lo que incrementará la duración del desarrollo en 3 semanas”

CARRETE
Costos
Alcance
Riesgos
Recursos
Calidad
Tiempo


---


La red de salud "Hospitales del Valle" necesita interconectar su Sede Central con una nueva Clínica de Urgencias ubicada a 12 km de distancia. Debido al alto congestión vehicular de la ciudad, el traslado terrestre de muestras de sangre urgentes y medicamentos críticos entre sedes tarda hasta 90 minutos, lo que pone en riesgo la vida de los pacientes.

El Directorio ha decidido financiar el proyecto "AeroMed Express": un sistema piloto de transporte autónomo mediante drones equipados con contenedores refrigerados con control de temperatura en tiempo real. El proyecto debe quedar 100% operativo en un plazo estricto de 6 semanas.

Plazo: 6 semanas (plazo límite por normativas de certificación hospitalaria).

Presupuesto: $25.000 USD. Debe realizar:

- EDT, Cronograma

- Objetivos (general y específicos), beneficios, alcance, entregables, criterios de aceptación, riesgos, roles

**Respuestas:**

Objetivo principal
	Interconectar su sede central con nueva clinica de urgencias a 12km de distancia.

Objetivos específicos
- Reducción de tiempo: Disminuir un 70% en el tiempo total de traslado
- Cumplimiento normativo
- Disminuir costes de traslado en 30%
- Despliegue de  10 unidades de drones en paralelo simultáneamente

Beneficios
- Menor tiempo de traslado
- Mejoras de autonomía, al no depender de carreteras o tráfico
- Menor costo de operación
- Paralelización de drones de hasta 10 unidades

Alcance
- Inclusiones
	- 10 drones operativos
	- Algoritmo de ruteo para punto A y B
	- 2 Estaciones de despliegue 
	- Baterías extraibles
	- Desarrollo de dashboard de monitoreo en tiempo real
	- Capacitación al personal de laboratorio en ambas sedes para uso del dron
	- Tramitacion de permisos aereos
- Exclusiones
	- Aplicacion movil
	- Almacenamiento del dron para otras cosas que no sean muestras o medicamentos críticos
	- Algoritmo de ruteo con respuesta en tiempo real
	- Extensión de servicio a otras sedes adicionales

| Entregables                                | Criterio de aceptación                                                                                                                      |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Flota de drones de 10 unidades             | Los drones concretan el trayecto autonomo de 12km y mantener el material en buenas condiciones                                              |
| Capacitación de personal para uso del dron | Que sean capaces de manejar los drones por su cuenta                                                                                        |
| Sistema de dashboard iot                   | Capacidad de monitorizar estado del dron en cada momento                                                                                    |
| Baterias extraibles                        | Facilidad de cambio de baterías del dron para recargarlos en la estación, además de tener una duración de 4h como mínimo del dron operativo |
| Estaciones de operacion                    | Deben tener el espacio suficiente para almacenar, mantener y operar los drones desde cada estación.                                         |
| Certificados y permisos                    | Los drones cumplen con la normativa de iot aereos y leyes, autorizando su funcionamiento.                                                   |

Riesgos
- Posible colisión de drones en medio del trayecto con x objeto o dron
- Capacidad suficiente de la batería para que no se acabe en medio del trayecto
- Almacenamento del dron lo suficientemente seguro como para evitar caidas de la muestra o medicamento
- Pérdida de comunicación del dron en medio del trayecto
- Riesgo temporal: Posibilidad de no desarrollar el proyecto a tiempo dentro del cronograma establecido
- Presupuesto: Posibilidad de superar el presupuesto establecido

Roles
- *Sponsor*
- *Proyect Manager*
- Ingeniero de drones y hardware
- Ingeniero informático
- Jefe de laboratorio (cliente interno)
- *Encargado regulatorio*


**Cronograma**
1. Kick-off -> Compra de equipamiento -> Solicitud de permisos
2. Adecuación de terrenos -> Configuración IoT
3. Hito 1: Avance de algoritmo de ruteo
4. Adquisición de permisos -> Pruebas de vuelo
5. Hito 2: Pruebas con carga simulada -> Capacitación personal
6. Vuelo piloto oficial -> Firma de aceptación

**EDT**

1. Gestión del proyecto
	1. Planificacion inicial y kick-off
	2. Definicion de responsables
	3. Seguimiento del proyecto
	4. Gestión de riesgos
2. Infraestructura y diseño
	1. Adquisición de drones 
	2. Integración de sensores IoT
	3. Adecuación de zonas de despliegue
3. Software y telemetría
	1. Configuración de rutas autonomas
	2. Despliegue del dashboard
	3. Pruebas de alertas térmicas y riesgos 
4. Regulaciones y seguridad
	1. Regulación de permisos 
	2. Protocolo de seguridad y custodia
5. Documentación y Capacitacióm
	1. Prueba de vuelo técnico sin carga
	2. Simulación de vuelo con carga
	3. Capacitación a personal médico y de laboratorios
	4. Capacitación de dashboard
6. Producción
	1. Despliegue de drones 
	2. Entrega de manuales
	3. Publicar dashboard
	4. Entrada de operación oficial

---

"AquaSens IoT" – Monitoreo Automático de Calidad del Agua

La empresa agrícola "Salmones del Sur" enfrenta pérdidas millonarias por variaciones imprevistas en la temperatura y los niveles de oxígeno disuelto en sus centros de cultivo flotantes en la Región de Los Lagos. Actualmente, las mediciones se realizan manualmente por personal técnico en lancha dos veces al día, lo que impide detectar a tiempo floraciones de algas o caídas bruscas de oxígeno, provocando mortalidad masiva de peces.

El Directorio ha aprobado el proyecto **"AquaSens IoT"**: un sistema de monitoreo automatizado basado en 4 boyas inteligentes equipadas con sensores sumergibles de oxígeno, pH y temperatura, transmisión de datos inalámbrica en tiempo real y una plataforma web/móvil con alertas críticas automáticas al equipo de operaciones.

Restricciones:
- Plazo: 8 semanas estricto (límite antes del inicio de la temporada de verano, donde aumenta el riesgo de mortandades).
- Presupuesto: $35.000 USD.

**Se pide desarrollar:**

1. Objetivos (General y Específicos SMART) y Beneficios.
2. Alcance (Inclusiones y Exclusiones).
3. Entregables y Criterios de Aceptación.
4. Roles del Proyecto.
5. Estructura de Desglose del Trabajo (EDT / WBS).
6. Cronograma e Hitos (8 Semanas).
7. Identificación y Redacción Formal de 3 Riesgos (Causa -> Evento -> Impacto).

RESPUESTAS:

Objetivo general: 
	Instalar una red IoT de monitoreo automatizado de 4 boyas inteligentes equipadas con sensores sumergibles, con transmisión inalámbrica en tiempo real, junto con plataforma web/movil para el equipo de operaciones.
Objetivos específicos:
- Funcionamiento con 99,9% de disponibilidad de boyas
- Conectar la red inalámbrica, con registro de 2% de todos los datos solo para enviar las variaciones
- Desarrollar plataforma web
- Asegurar monitoreo de sensores (oxigeno, ph, temperatura)
- Desarrollar algoritmo para detectar floraciones de algas y/o caidas bruscas de oxígeno

Beneficios
- Automatización del proceso (antes tenían que enviar a personas cada 2 dias)
- Ahorro de costos en personal
- Predicción de caídas ante floraciones de algas y/o caidas bruscas de oxígeno
- Monitorización en plataforma web digitalmente - Trazabilidad analítica
- Mitigación de pérdidas
- Eficiencia operativa

Alcance
- Inclusiones
	- Plataforma web de monitoreo
	- Instalación de 4 boyas inteligentes
	- Funcionamiento correcto de los sensores
	- Desarrollo de base de datos para almacenar registro de los sensores
	Exclusiones
	- Predicción a futuro de floraciones de algas y/o caidas bruscas
	- Plataforma móvil
	- Desarrollo de algoritmo Y/o instalaciones fuera de la empresa
	- Instalación de más de 4 boyas



| Entregables              | Criterio de Aceptación                                                      |
| ------------------------ | --------------------------------------------------------------------------- |
| Boyas instaladas         | Instalación de 4 boyas con sensores funcionales                             |
| Capacitación de uso      | Capacitación para manejo de plataforma web de monitoreo                     |
| Plataforma web/Dashboard | Trazabilidad analítica en tiempo real de las variaciones de oxígeno y algas |
| Personal certificado     | Todos los operadores aprueban el taller práctico de uso del sistema         |

Roles 
1. Sponsor
2. Project Manager
3. Ingeniero informático (hardware)
4. Ingeniero de software
5. Cliente -> Agricolas de salmones 

EDT

1. Gestión del proyecto
	1. Planificación kick-off
2. Infraestructura y diseño
3. Software y telemetría
4. Regularizacion
5. Documentación
6. Producción


Riesgo: Causa -> Evento -> Impacto
