
# Clase 1 
09/03/26

## Intro
El término fue inventado en 1999

Lo *smart* viene en la capacidad de interconexión y en el intercambio de datos que hagas con los demás objetos, un solo tipo de red para todo
- *Smart Object* no implica inteligencia

habian 2 problemas principales:
1. La forma de transmitir info (paquets con datos)
2. Seguridad y privacidad
   
- No todas las tecnologias se incorporan masivamente de un dia para otro

- ¿Existe la portabilidad entre ciertos servicios?
	Debería, pero no existe por la competencia entre empresas

- Interfaz inalámbrica: Wifi, Buetooth, datos móviles

la idea de un estándar es mantener unidad entre empresas para una misma "herramienta", que mantengan a sus usuarios no por las capacidades, sino por su "conveniencia"

##### ¿Qué cosas califica como IoT?

- Un celular *NO* califica como *IoT*
- Un mouse podría serlo
- Aire acondicionado  *SI* es *IoT*, comunica temperatura (1 parámetro)

- **Personalidad**
	- Pueden ser *fuentes de informacion*: sensores
	- o *Destinos* y ser actuadores

En un sistema orientado al cloud computing exclusivamente, se toman de *forma jerárquica*
- La energía es fundamental

Pero un sistema donde los nodos se conectan entre ellos
	Se denomina *Fog computing* (intermedio), parte del concepto de Internet of Everithing

1. Instalado en la infraestructura
2. Covertura por redes inalámbricas
3. Usando de manera satelital

### Redes tradicionales
- Estaciones base conectadasa a un *backbone*
- Elementos móviles conectados de manera inalámbrica a la estación base

### Redes de Nodos sensores (a estudiar)
Red de nodos con sensores comunicándose entre sí sin tener que usar servicio de nadie

- Multisalto
- Solo un salto
- Puente para otras redes
- Gateways simples o multiples
- Topologías Mesh / Estrella / Árbol

Una métrica es *tiempo de vida de red* para medir la eficacia de una red
La existencia de caminos alternativos es buena (like)

Una cosa es la topología, y otra es la red que armamos encima de este, usara parte de la topologia disponible para comunicar. Uso sólo los convenientes 
	¿Estan todos disponibles? Si
	¿Debería usar todos? No

## Características de Nodos

1. Corto alcance (50-100m) o Largo alcance con limitaciones grandes 
2. Poca capacidad de procesamiento 
	Buscamos el mínimo hardware para hacer lo mismo, ser eficiente es mejor
3. Alimentados a Batería 
	TX, RX, Sensor
4. Poca capacidad de Almacenamiento
	 Tablas limitadas, tamaño del programa, registro limitado 
5. Relojes de baja precisión
	Sincronización (muy importante), compensación
6. Tamaño
	Acceso, Ubicación, Peso, Gabinetes estandarizados, Antenas o Mantenibilidad
7. Interfaces de programación y comunicación
	Conectores, estándares
8. Sistemas Operativos, Stacks, Lenguajes de programación
	Disponibilidad
9. Robusto físicamente
	Ambiente hostil: vibraciones, temperatura, químicos..
10. Auto-Organizarse
	Construcción de rutas, intercambio de claves, estabilidad
11. Sincronización
	Sistemas TDMA (time division multiple access) o Híbridos CSMA/TDMA
12. Mantener bajo consumo
	Duración de batería
13. Redundancia
		Lograr recuperarse de fallas de nodos (Redundancia de topografía, reconstrucción de vias)
14. Seguridad
    Encriptación en capas, distribución de claves
15. Incluir Identificación, autentificación
16. Proveer localización 
	Para georeferenciación y/o asignación de recursos


## Problemas

Si uno no tiene registro de errores o de lo que está pasando, uno no puede hacer mucho para solucionar.

1. Control de Acceso
2. Enrutamiento
3. Topología
4. Recursos
5. Consumo
6. Gestión
7. Transporte de Datos
8. Movilidad
9. Regulación
	Ancho de banda, potencia, Canalización, Zonas

## Datos

Patrones de funcionamiento

-  Envío *periódico* de datos
- Detección de *Eventos*	
- Aproximación de funciones
	Puedo hacer un conjunto de mensajes de distintos sensores y transmitirlo como uno
- Detección de bordes
	Pregunto cuando hay algún cambio
- Seguimiento de objetos
- Consultas a la red
- Pre-procesamiento en la red
- Redes orientas a contenidos
- ¿Tiempo real? -> Garantías de Máximo retardo y Pérdida de datos

*Priorización* de información a mandar es crucial también

## ¿Cómo se distribuyen los Nodos?

1. Al azar (Lanzados desde un dron, avión)
2. Regularmente (Matricial)
3. De acuerdo a la *representavilidad de la variable* a medir (densidad variable)
4. Móviles (movimiento)
	Patrones regulares o irregulares de movimiento, movidos por una fuente externa por ej flujo de agua o petróleo

## Mantenimiento y Escalabilidad

### Mantenimiento

- Reemplazo de Baterías posible?
- Alimentación a partir de fuentes externas
	Sol, movimiento, vibraciones
- Duración esperada
- Detección de fallas
- Incorporación de nuevos nodos durante el funcionamiento de la red
- Contaminación posible

### Escalabilidad

- Limitaciones en direccionamiento/enrutamiento
- Limitaciones de recursos disponible: ¿reuso de recursos?
- Convivencia con otras redes en el mismo espectro / protocolo
- Sistema de captura asociado a  un proveedor



# Clase 2
12/03/26

## Arquitectura de IoT

Distintos participantes (*stackeholders*) tienen distintas visiones de la arquitectura de la IoT, donde existen proveedores como:

Existen proveedores de sistemas basados en Cloud Computing, proveedor de redes, sistemas de nodos/actuadores, entre otros. Generalmente son autónomos y que necesiten un humano al lado para funcionar (autónomo).

- Entes de *estandarización*
	*-> La idea es hablar el mismo idioma para comunicarnos*
	La idea es que la solución tenga mantenibilidad para el futuro.
	Debe cumplir, sino, no entro en la industria 
	SEC, seguridad eléctrica en Chile

- Consultoras
- Inversores en Tecnología
- Desarrolladores de Middleware y Sistemas Operativos
	La idea  es no preocuparse de problemas futuros, simplificando su instalación desde un inicio (mayor flexibilidad)

- Proveedores de soluciones basados en IoT

 - **Landscape 2018**
- Evolución de Gartner
	Gráfico de la expectación, caída y uso diario de tecnologías a través del tiempo

## Aplicaciones
Verticales de aplicación. Cuáles son las industrias que utilizan y a dónde encontraremos estos.

Agricultura, Salud, Industra, Seguridad, Home, Ambiente, Transporte, Militar, Instrumentación, Seguros (para saber a través de monitoreo si hay que aplicar algún seguro).

> Hay que entender el problema que estamos atacando para aplicar adecuadamente la solución.

### Transporte y Movilidad
- Monitoreo y Seguimiento de vehículos / flotas
- estado de vías ferreas
- Estructuras viales (puentes, túneles)
- Seguimiento de nivel de uso de transporte público
- Monitoreo de usuarios / fuerza de venta
- Trazabilidad

EJ) Tarjeta BIP
Es útil y cambia su valor interno rápidamente con los totems a una frecuencia de 5 MHz

QR: Quick response
# Clase 3
16/03/26
## Aplicaciones Pt. 2

### Entretención / Retail / Comercio

- Controles inalámbricos
- *Control de acceso*
- Monitoreo de fallas de juegos mecánicos
- Localización de usuarios
- Indicadores de precio
- Paneles de información
- Seguimiento de movimiento de usuarios

###  Industria

Monitoreo de:
- Refinerias 
- Vibraciones en túneles de minería
- Seguimiento en máquinas de minas a cielo abierto
- Fallas en rodillos de cintas transportadoras
- Smart Meters (Electricidad, agua, gas)
- Logística de basura
- Calidad eléctrica, consumos individuales de dispositivos
- Hoteles
	- Uso de recursos, detección de fallos
	- Iluminación de pasillos, logística de habitaciones

### Ambiente
Monitoreo de:
- Glaciares (movimiento, contaminación)
- Nivel de nieve para provisión de agua !!
- Flujo de agua en cuencas
- Avance de sedimentos y sólidos
- Sismos
- Incendios e inundaciones
- Desplazamientos de tierra y aludes
- Niveles de ríos y mareas

# Clase 4
19/03/26

## Aplicaciones Pt. 3

### Agricultura
Monitoreo de:
- Humedad y temperatura para el riego
- Niveles de fertilizantes
- Plagas
- Temperaturas en silos
	- Silo: Cilindros enormes contenedores de semillas
- Estado de animales (movilidad, temperatura)
- Seguridad perimetral
- Seguridad de alimento/liquidos
- Seguimiento en tambos
- Monitoreo de cámaras frigoríficas
- Seguimiento de cosechas manuales

















