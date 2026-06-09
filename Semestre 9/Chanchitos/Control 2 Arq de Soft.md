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
4. Capa de almacenamiento: Sistema físico de persistenciade datos

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
- tipos de datos
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


