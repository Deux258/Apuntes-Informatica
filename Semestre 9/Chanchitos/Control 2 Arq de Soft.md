## Patrones de Arquitectura

1. Patrones Simples
	1. Capas
	2. Tubos y Filtros
	3. Pizarrón
	4. Repositorio
2. Patrones para Sistemas Interactivos
	1. *MVC* Modelo Vista Controlador 
	2. *PAC* Presentación Abstracción Control
3. Patrones para Sistemas Adaptables
	1. MicroKernel
	2. Reflection

- Los simples buscan organizar y estructurar sistemas de forma clara y mantenible
- Los interactivos en la interacción entre el usuario y sistema. Separa interfaz, lógica y control
- Los Sistemas Adaptables para sistemas que deben cambiar, extenderse o personalizarse fácilmente.

- [p] Facilita el trabajo en equipo
- [p] Permite el uso de estándares
- [p] Asegura la división de responsabilidades

- [c] Puede generar rigidez técnica
- [c] Implica una curva de aprendizaje
- [c] Conlleva una dependencia técnica


## Patrones Simples

### Patrón de Capas
Separa las capas de forma secuencial con distintos niveles de abstracción. Usado para estructurar aplicaciones

*Para*: Necesidad de organizar el software en sistemas sin una estructura clara
*Solución*: Estructuración en esquema multi-capa, definiendo una capa base con el nivle de abstracción más bajo, donde irá avanzando capa por capa

Esta puede incluir:
1. Capa de presentación: Interacción con el usuario
2. Capa de lógica de negocio: Contiene las reglas, procesos y validaciones principales
3. Capa de acceso a datos: Comuncación con base de datos o servicios externos
4. Capa de almacenamiento: Sistema físico de persistencia de datos

Cada capa tiene su complejidad interna y entrega servicios a la capa superior.

![[Pasted image 20260608205234.png]]


- [p] Reutilización: Una capa completa puede reutilizarse en distintas apps
- [p] Mantenibilidad
- [p] Estandarización

- [c] Baja eficiencia: Las soluciones deben atravesar múltiples capas antes de obtener una respuesta.
- [c] Complejidad de definición: Diseñarlo es una paja

###### EJERCICIO
Una biblioteca pública desea automatizar su proceso operativo de préstamo de libros, el cual
actualmente es manual. El proceso consta de los siguientes pasos:
1. El cliente busca un libro en el catálogo digital de la biblioteca.
2. El bibliotecario verifica si el cliente tiene multas o préstamos vencidos.
3. Si el cliente está habilitado, el bibliotecario verifica la disponibilidad del libro
seleccionado.
4. Si está disponible, el bibliotecario registra el préstamo en el sistema de inventario.
5. El bibliotecario notifica al sistema externo de correo para enviar un comprobante al
cliente.
6. Hecho el registro y enviada la notificación, se le entrega el libro al cliente.

Se pide diseñar este sistema utilizando el patrón de Capas

1. Interfaz
	- Cliente
	- Bibliotecario
2. Validacion
	- Multas
	- Prestamos vencidos
	- Si cliente está habilitado -> Bibliotecario verifica si hay libro
3. Aplicacion
	- Confirmar préstamos o multas
	- Invocar libro si esta disponible
	- Notificar el comprobante tras registro exitoso
4. Sist. Externos
	- Sist. correos para comprobantes
5. Acceso a datos
	- Acceso a multas o prestamos - Antecedentes del cliente
	- Informacion de los libros
	- Registro de prestamos de libros y descontarlo
6. Datos
	- Libros
	- Multas
	- Registros
	- Mecanismos fisicos a los datos de inventario, catalogo
	- Base de datos -> Servidor fisico


### Patrón de Tubos y Filtros
Ideal para sistemas que procesan flujos de datos, diseñado para forma *secuencial*.

Tubos (pipes) -> Lugares por donde viaja 
Filtro (filter) -> Transforma la entrada en salida (como una función)

- Cada filtro es independiente y muy separado
- El tubo no altera los datos

*Para*: Complejidad de procesar grandes cantidades de info por una unica estructura monolítica.
*Solución*: Organizar el sistema por tubos y filtros para dividir la tarea en pequeñas actividades e independientes.

- Generalmente usan FIFO

![[Pasted image 20260608212619.png]]

- [p] Arquitectura flexible
- [p] Construcción Independiente
- [p] Eficiencia
- [p] No requiere archivos intermedios
- [p] Información no compartida

- [c] Conversión de datos: Puede ser necesario transformar los datos entre filtros
- [c] Manejo de errores: Detectar, propagar, y controlar errores es una paja

###### Ejemplo
Una compañía de seguros requiere mejorar su proceso de venta de seguros. En la
actualidad, todo el proceso es manual y consta de los siguientes pasos:
1. Confección de la propuesta de seguro en la que se individualiza al cliente y el objeto a asegurar.
2. Evaluación de la propuesta por el depto de Análisis de Riesgo para determinar el valor de
la póliza.
3. Determinación de las condiciones de pago, hecha por el depto de Finanzas.
4. Revisión de la propuesta, a cargo del depto de Siniestros.
5. Envío de la propuesta de seguro al cliente, coordinado por el depto de Distribución.
6. Recepción de la propuesta aceptada por el cliente, en el depto de Ingreso de
Documentos archivo de la propuesta en el departamento de Seguros.

Se pide diseñar este sistema utilizando el patrón de Tubos y Filtros.

![[Pasted image 20260608212929.png]]


### Patrón de Pizarrón
Espacio común donde se obtienen datos y se dejan resultados.

*Para*: Resolver problemas demasiado complejos para un único sistema y requiere varios modulos especializados
*Solución*: Usar almacenamiento centralizado (Pizarrón) como espacio de trabajo compartido y global.

#### Características
En el pizarron se almacena:
- El estado actual del problema
- El progreso hacia la solución
- Datos parciales
- Hipótesis
- Resultados intermedios
- Diccionario de datos para que todos los sistemas comprendan la información almacenada

#### Controlador
Es el encargado de coordinar la ejecución de los distintos sistemas que participan en la solución.

- Monitorear continuamente el estado actual del pizarrón
- Analiza el progreso
- Decide qué sistema debe ejecutarse a continuación
Toma decisiones en base a:
- Los datos disponibles
- Soluciones parciales
- Estado actual del problema
- Objetivo final

#### Diccionario de Datos
Documento central que define y describe toda la info almacenada en el pizarrón. Se asegura que todos los sistemas interpreten los datos de la misma forma

- Nombres
- Tipos de datos
- Formatos
- Significado
- Unidades
- Restricciones


![[Pasted image 20260608213301.png]]

#### Casos de uso
1. Reconocimiento de voz
2. Reconocimiento de imagenes y texto
3. Soporte a Toma de Decisiones
4. Sistemas de IA

- [p] Arquitectura flexible
- [p] Modularidad y paralelismo
- [p] Construcción Independiente

- [c] Baja eficiencia: Monitoreo constante de pizarrón y la coordinación entre especialistas lo nerfean
- [c] Cuello de botella: Representa un punto único de acceso para todos los especialistas
- [c] Riesgo de Acoplamiento: Todos dependen de la estructura, formato y semántica de los datos. 

###### Ejemplo
Un sistema de asistencia virtual requiere implementar un mecanismo de reconocimiento de voz capaz de transformar señales de audio en texto escrito. En la actualidad, el procesamiento de audio presenta dificultades debido al ruido, variaciones de pronunciación y complejidad del lenguaje hablado. El proceso consta de las siguientes etapas:
1. El sistema recibe una señal de audio desde el micrófono del usuario.
2. Un módulo analiza las características acústicas del audio recibido.
3. Otro sistema identifica fonemas y sonidos del lenguaje.
4. Un especialista construye posibles palabras a partir de los fonemas detectados.
5. Otro módulo analiza el contexto y valida la gramática de las frases.
6. Finalmente, el sistema genera el texto escrito correspondiente al audio procesado.
Se pide diseñar este sistema utilizando el patrón de Pizarrón.


- Controlador
	- Revisa el estado del pizarrón
	- Analiza el contenido almacenado
	- Decide que módulos deben ser activados
- Módulos
	- Extracción de características
	- Reconocimiento de fonemas
	- Construcción de palabras
	- Análisis gramatical
	- Corrección de errores
- Pizarrón
	- Almacena el audio original
	- Recibe las características extraídas
	- Almacena fonemas detectados
	- Recibe las palabras propuestas


### Patrón de Repositorio
Centraliza el acceso y manejo de datos por un intermediario llamado repositorio. 
NO acceden directamente a la base de datos, sino a través de este repositorio

*Para*: Sistemas grandes donde multiples aplicaciones necesitan acceder y modificar grandes cantidades de datos constantemente
*Solución*: Estructuracion multi-capa, definiendo una capa base con el nivel de abstracción más bajo, en donde el sistema ira avanzando capa por capa.

- Interfaz comun para operaciones CRUD
- Desacopla la lógica con almacenamiento fisico de datos
- Multiples aplicaciones trabajan con informacion consistente
- Facilita el mantenimiento por centralización de datos

#### Casos de Uso
- Consultar datos
- Almacenar info
- Actualizar registros
- Eliminar datos

> Los componentes no acceden directamente a las bases de datos físicas, usan una interfaz común

![[Pasted image 20260609111158.png]]

- [p] Centralización de Datos
- [p] Desacoplamiento
- [p] Mantenimiento  isi
- [p] Reutilizacion 
- [p] Integracion de multiples fuentes

- [c] Cuello de botella
- [c] Complejidad de implementacion: Desarrollo de interfaz comun
- [c] Dependencia del repositorio
- [c] Posible pérdida de rendimiento

###### Ejemplo
Una cadena de hospitales requiere modernizar su sistema de gestión clínica. Actualmente, la
información de pacientes, médicos, exámenes y tratamientos se encuentra distribuida en distintas bases de datos y plataformas utilizadas por diferentes áreas del hospital.
El sistema debe permitir que:
1. El módulo de atención médica consulte historiales clínicos,
2. El laboratorio registre resultados de exámenes,
3. El área de farmacia actualice medicamentos entregados,
4. El sistema administrativo gestione pagos y citas médicas.
Todas las aplicaciones necesitan acceder y modificar información de manera consistente,
evitando duplicación y acceso directo a las bases de datos.
Se pide diseñar este sistema utilizando el patrón de Repositorio

- Definir el Repositorio
	El repositorio corresponde al componente central del sistema hospitalario y actúa como una capa intermedia entre las aplicaciones y las bases de datos. Su función es centralizar el acceso a la información clínica y administrativa, proporcionando una interfaz común para consultar, almacenar, actualizar y eliminar datos.
	En el repositorio se maneja información como:
	- Pacientes
	- Historiales clínicos
	- Exámenes
	- Tratamientos
	- Medicamentos
	- Pagos y citas médicas
	Los módulos del sistema no acceden directamente a las bases de datos físicas, sino únicamente mediante el repositorio, asegurando consistencia y desacoplamiento
- Definir los Componentes
	Los componentes corresponden a los distintos módulos del hospital que ejecutan la lógica de negocio y utilizan el repositorio para acceder a la información.
	Por ejemplo:
	- Atención médica consulta historiales y registra diagnósticos
	- Laboratorio almacena resultados de exámenes
	- Farmacia actualiza medicamentos entregados
	- Administración gestiona pagos y citas
	Cada componente trabaja de manera independiente, pero comparte la misma fuente lógica de información mediante el repositorio central.

![[Pasted image 20260609111158.png]]


## Patrones para Sistemas Interactivos

### MVC - Modelo Vista Controlador

1. Modelo: Datos y lógica esencial
2. Vista: Comunicación con el usuario
3. Controlador: Gestión de cambios

Se aplica a *sistemas interactivos* con interfaz flexible que necesita evolucionar y cambiar con frecuencia.

- Busca desacoplar la interfaz de usuario de la lógica del negocio
- Usa al controlador como intermediario que hace posible este desacoplamiento

#### Modelo
- Funcionalidad esencial y lógica de negocio
- Gestión de datos persistentes
- Independencia de Vista y Controlador -> permite reutilizar codigo y bajo acoplamiento

#### Vista
- Comunicación con el usuario
- Presentación de datos del Modelo
- Envío de requerimientos al controlador
- Múltiples representaciones de los datos

#### Controlador
- Administrador del comportamiento del sistema
- Recepción de eventos desde la vista
- Interacción con el Modelo
- Coordinación de la actualización de la Vista

##### Interacción
1. El usuario interactúa con la Vista
2. La vista notifica al controlador sobre la acción
3. El controlador determina qué significa la acción y solicita al Modelo realizar la lógica necesaria
4. El Modelo *ejecuta la lógica*
5. El Modelo *notifica* a la Vista que sus datos han cambiado
6. La vista solicita los datos actualizados *al modelo* y se redibuja para mostrarlos al usuario

![[Pasted image 20260609112323.png]]



- [p] Modelo soporta multiples vistas
- [p] Flexible, mantenible, adaptable
- [p] Frameworks implementan MVC

- [c] Modelo acoplado con vistas y controladores
- [c] Vistas sin acceso directo a los datos (ineficiencia)
- [c] Complejidad: cantidad de código y coordinación entre ellos


#### Casos de Uso
- Sistema de comercio electrónico (ej pasteleria)
- Sistema académico universitario

###### Ejemplo
Una pastelería de barrio quiere abrirse al comercio electrónico. Para ello, requiere el desarrollo de un sistema que cubra los siguientes requerimientos funcionales:
- Recepción de pedidos online
- Disponibilidad de diversos medios de pago (webpay, mercadoPago, transferencias, etc.)
- Organización de los envíos a domicilio
- Gestión de los repartidores
- Estadísticas de venta, diaria, semanal, mensual, anual
Se pide:
1. Diseño del sistema usando el patrón MVC.
2. Diagrama global de la solución indicando como se va a satisfacer la funcionalidad
requerida.


Vista
- Administrador: Gestionar usuarios, registro de datos, control de app, estadisticas de venta
- Cliente: Vista de pasteles, compras, estado del pedido, login
- Repartidor: Pedidos a realizar, direcciones, historial de pedido, pedidos listoss
Modelo
- Estadísticas de venta: diaria, semanal, mensual, anual
- Gestion de clientes
- Gestion de repartidores
- Gestion de stock
- Envios 
- Gestion de pedidos
Controlador
- Control_Pedidos
	- Navegacion catalogo
	- CRUD pedidos
	- Control pagos
	- Interfaz externa medios de pagos
- Control_Envios
	- CRUD envios
	- Control repartidores
	- CRUD repartidores
- Control_Estadisticas
	- Generacion estadisticas
  

![[Pasted image 20260609114855.png]]


### Modelo PAC
Organiza el sistema en *agentes*, que se comunican entre sí para realizar distintas tareas de la app/sistema. Cada agente es un *modulo autónomo* que encapsula una funcionalidad específica, compuesto por 3 elementos:

1. Presentación -> Interfaz de usuario
2. Abstracción -> Datos y lógica de negocio
3. Control -> Coordinación y comunicación

*Para*: Sistemas interactivos complejos, ya que permite dividir la app en *subsistemas especializados* que trabajan de forma independiente, pero colaboran entre sí

- Facilita la modularidad, mantenimiento y escalabilidad del sistema

#### Jerarquía PAC

1. **Alto nivel** -> Funcionalidad principal e interacción global con el usuario. También coordina a los agentes intermedios para que trabajen de forma conjunta.

2. **Intermedio** -> Coordinador, facilita la comunicacion entre agentes. Distribuye tareas a agentes de bajo nivel y oculta la complejidad de componentes inferiores al resto.

3. **Bajo nivel** -> Tareas especificas. Interactua directamente con el usuario, dispositivos o recursos externos. Mantiene encapsulada la lógica de una tarea especifica (alcance limitdado).

![[Pasted image 20260609115714.png]]


- [p] Asigna responsabilidades específicas
- [p] Funcionamiento independiente
- [p] Soporta multitarea

- [c] Sistema complejo
- [c] Baja eficiencia: comunicación entre agentes y componentes internos de cada agente
- [c] Complejo mecanismo de control: Coordinación entre agentes - Mientras más, más pajero

#### Casos de Uso
- Aplicaciones con Interfaces complejas (cada ventana puede agregarse como agente)
- Sistemas de control y monitoreo
- Sistemas Multiagente e IA

###### Ejemplo
Una empresa desea ampliar sus canales de venta para llegar a más clientes. Actualmente
vende únicamente en tiendas físicas, pero quiere incorporar un sitio web, una aplicación móvil y un Call Center. Aunque cada canal debe funcionar de forma independiente y ofrecer una experiencia adaptada a sus usuarios, todos deben compartir la misma información de
inventario, las reglas de negocio y el proceso de facturación para garantizar consistencia en
las operaciones.
Para resolver este problema se pide utilizar el patrón PAC.

- Sistema de ventas
- Pagina web
- Tienda
- Inventario
- Call center

Sistema de ventas (alto nivel)
- Presentación 
	- Dashboard de ventas
	- Reportes de todos los canales
- Abstracción 
	- Reglas globales de negocio
	- Facturación centralizada
	- Gestión global de clientes
- Control 
	- Coordinación entre todos los agentes
	- Distribución de solicitudes
	- Sincronizacion de info entre canales



![[Pasted image 20260609120708.png]]



## Posibles preguntas

- - - Control 2 - - - Analice los párrafos siguientes e indique si está de acuerdo con lo que expresan. En la eventualidad de que discrepe con lo que dicen, debe indicar cómo se corregiría.

**1.** En una arquitectura orientada a servicios (SOA), la comunicación entre los servicios y los clientes se realiza a través de un bus central llamado Enterprise Service Bus (ESB). El ESB actúa como una base de datos que guarda el estado interno y persistente del negocio (como pedidos o usuarios) para permitir que los servicios se comuniquen directamente entre sí, fomentando un fuerte acoplamiento que garantiza la integridad del sistema.

**2.** El patrón de Pizarrón se utiliza para resolver problemas complejos donde múltiples módulos especializados colaboran aportando a un espacio centralizado. Dado que es idéntico funcionalmente al patrón de Repositorio, en el Pizarrón es el propio espacio de almacenamiento de datos el que toma el rol de controlador, analizando los resultados intermedios y decidiendo qué módulo especializado debe ejecutarse en el siguiente paso.

**3.** En el patrón de Capas, el sistema se divide en niveles jerárquicos con distintas responsabilidades. Una de las principales ventajas de este patrón es la alta eficiencia y rendimiento que otorga, dado que permite que una petición de la capa superior (como la Interfaz de Usuario) salte directamente a la capa de Datos si no requiere procesamiento en las capas intermedias, evitando así la sobrecarga de comunicación.

**4.** Dentro de los patrones interactivos, en el patrón MVC (Modelo Vista Controlador) la Vista se comunica directamente con el Modelo para enviarle las interacciones del usuario y actualizar los datos. De forma similar, en el patrón PAC (Presentación Abstracción Control), el componente de Presentación contiene la lógica de negocio básica para evitar que el Control se sobrecargue con validaciones simples del usuario.

---

- (1) correcto. (2) Incorrecto, el ESB hace unicamente de intermediario o mensajero entre servicios, no almacena la lógica del negocio.
- (1) correcto. (2) Falso, no es como el patrón de repositorio, no almacena datos masivamente si no que se mezclan ideas para un problema complejo, ademas de no poseer una base de datos como tal.
- (1) correcto. (2) Falso, tiene bajo performance debido a que se tiene que comunicar verticalmente con todas las capas para poder responder. Para poder enviar un mensaje, tiene que acceder a la capa de datos, pasando por todas las capas.
- (1) Incorrecto, el controlador hace de intermediario entre la vista y modelo. (2) Incorrecto, Abstracción es el encargado de llevar la logica del negocio.


**1. Sobre el patrón SOA y el ESB**

- **Tu respuesta:** (1) Correcto. (2) Incorrecto, el ESB hace únicamente de intermediario o mensajero entre servicios, no almacena la lógica del negocio.
- **Corrección:** ¡Estás en lo correcto! La primera frase es cierta, pero la segunda tiene varios errores que detectaste muy bien. Efectivamente, el ESB es principalmente "stateless" (sin estado), por lo que no guarda información persistente del negocio ni implementa la lógica principal.
- _Detalle adicional para tu estudio:_ Además de no guardar el estado del negocio, el ESB **evita** que los servicios se comuniquen directamente entre sí (conexión punto a punto), actuando como un único punto de intercambio de mensajes. Gracias a esto, el patrón SOA promueve el **bajo acoplamiento** en lugar de un fuerte acoplamiento como afirmaba el párrafo trampa.

**2. Sobre el patrón Pizarrón**

- **Tu respuesta:** (1) Correcto. (2) Falso, no es como el patrón de repositorio, no almacena datos masivamente si no que se mezclan ideas para un problema complejo, ademas de no poseer una base de datos como tal.
- **Corrección:** ¡Muy bien detectado! La primera parte es correcta y la segunda es falsa. Tienes razón en que su objetivo es la colaboración de expertos (ideas) para un problema complejo sin una ruta algorítmica clara, diferenciándose así del Repositorio tradicional.
- _Detalle adicional para tu estudio:_ El otro error grave del párrafo original era afirmar que el propio espacio de almacenamiento toma el rol de controlador. En realidad, en el patrón Pizarrón existe un componente separado llamado **Controlador Centralizado**, el cual monitorea el pizarrón y decide qué sistema especializado debe ejecutarse a continuación.

**3. Sobre el patrón de Capas**

- **Tu respuesta:** (1) Correcto. (2) Falso, tiene bajo performance debido a que se tiene que comunicar verticalmente con todas las capas para poder responder. Para poder enviar un mensaje, tiene que acceder a la capa de datos, pasando por todas las capas.
- **Corrección:** ¡Totalmente correcto y completo! Diste justo en el clavo. Una de las desventajas del patrón de Capas es su "baja eficiencia" porque las solicitudes deben atravesar múltiples capas antes de obtener una respuesta. Además, una regla estricta de este patrón es que la capa _K_ solamente puede comunicarse con la capa inmediatamente inferior o superior (_K-1_ o _K+1_), por lo que **no se pueden saltar capas**.

**4. Sobre los patrones interactivos (MVC y PAC)**

- **Tu respuesta:** (1) Incorrecto, el controlador hace de intermediario entre la vista y modelo. (2) Incorrecto, Abstracción es el encargado de llevar la logica del negocio.
- **Corrección:** ¡Excelente respuesta! Resolviste correctamente ambas trampas del párrafo. En MVC, la Vista y el Modelo no se comunican directamente; toda interacción pasa por el Controlador, quien funciona como administrador e intermediario. Por su parte, en el patrón PAC, la capa de Presentación **no contiene lógica de negocio** ni almacena los datos principales. Como bien indicas, esa es la función exclusiva del componente de Abstracción.

