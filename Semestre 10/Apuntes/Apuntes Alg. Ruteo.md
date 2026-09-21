# Guión de presentación — Red de Drones para Detección y Vigilancia de Incendios Forestales

Duración estimada total: 8–10 min (13 diapositivas). Las primeras 4 diapositivas están desarrolladas en detalle porque son las que fijan el marco del resto de la exposición: si el público entiende bien el problema, el paper base y la hipótesis, todo lo que viene después (infraestructura, metadata, amenazas) se explica solo.

## Diapositiva 1 — Portada

**Tiempo sugerido: 20–30 seg**

"Buenas [tardes/días]. Somos [Diego Muñoz, Ignacio Pastén, Eduardo Escalona y Diego Hidalgo], y venimos a presentar el primer informe del proyecto _Red de Drones para Detección y Vigilancia de Incendios Forestales_, desarrollado para el curso de Algoritmos de Ruteo y Redes Resilientes con el profesor Nicolás Boettcher."

**Objetivo de esta diapositiva:** presentarse y anclar el tema en una frase. No hay que detenerse en contenido — es el "handshake" con el público. Pasa rápido a la siguiente.


## Diapositiva 2 — Contexto / Trabajo Relacionado

**Tiempo sugerido: 1.5–2 min (la más densa de las primeras 4)**

Esta diapositiva cumple dos funciones a la vez —contexto del problema y presentación del paper base—, así que conviene dividir el discurso en dos bloques con una transición clara.

**Bloque 1 — Contexto (30 seg):**

> "Chile es uno de los países más expuestos a incendios forestales del hemisferio sur. Y el dato clave para entender por qué este proyecto importa es este: el tiempo que pasa entre que un foco se inicia y que alguien lo detecta no aumenta linealmente el daño — lo aumenta de forma _no lineal_. Cada minuto perdido en detección se traduce en mucha más superficie quemada y más riesgo para las personas. Por eso el problema central no es apagar incendios, es _detectarlos antes_."

**Bloque 2 — Trabajo relacionado / RSUPP (60–75 seg):**

> "Para no partir de cero, tomamos como línea base un paper real: Xu, Li y Zhang, 2022, publicado en la revista _Forests_ de MDPI. Ellos proponen un método llamado RSUPP para planificar el patrullaje de drones forestales.
> 
> ¿Cómo funciona? Primero toman un mapa de riesgo de incendio —estático, calculado de antemano— y dividen el área en subáreas usando un algoritmo de clustering, Gaussian Mixture. Luego, para cada subárea, calculan una ruta cerrada tipo _problema del vendedor viajero_ usando una red neuronal llamada RSOM, que arma un ciclo que visita los puntos de mayor riesgo con la menor distancia posible.
> 
> Lo validaron en un parque forestal en Nanjing, China, y les fue bien: su método cubre significativamente más puntos de alto riesgo que un patrullaje aleatorio, con la misma distancia de vuelo."

**Transición hacia la problemática (10 seg):**

> "El problema es que esa ruta es única y fija. Y ahí es donde entra nuestra propuesta — pero antes, veamos por qué eso es justamente el problema que queremos resolver."

**Nota de apoyo visual:** en la slide aparecen los tres sub-bloques "Método RSUPP / Ruta Cerrada / Validación Exitosa" — puedes usarlos como guía de orden al hablar (qué es → cómo calcula la ruta → qué tan bien funcionó), en vez de leerlos literalmente.


## Diapositiva 3 — Problemática

**Tiempo sugerido: 1.5 min**

> "Hoy en Chile existen varias formas de detectar incendios, pero todas tienen un punto débil.
> 
> La detección satelital, como el sistema FIRMS de la NASA, tiene una resolución de entre 375 metros y 1 kilómetro, y pasa por el mismo punto solo cada varias horas — un foco puede crecer mucho antes de ser confirmado.
> 
> Las torres de vigilancia y las brigadas de CONAF tienen cobertura limitada geográficamente y dependen de que alguien _vea_ el humo — de día, con buena visibilidad.
> 
> Y la vigilancia aérea tripulada es efectiva, pero cara, y no se puede mantener de forma persistente sobre una zona.
> 
> Ahí surge la idea obvia: usar drones. Pero un dron —o incluso una ruta de patrullaje como la de RSUPP— operando solo, es un **punto único de falla**. Si un tramo de la ruta se vuelve inviable —por un obstáculo, por mal clima, por una zona restringida— toda la misión se cae."

**Cierre — la frase que hay que dejar clara (léela casi textual, es la tesis del proyecto):**

> "Nuestra problemática central es la ausencia de una infraestructura de red geolocalizada y de un esquema de ruteo que permita a una flota de drones mantener cobertura de detección temprana de forma **resiliente** ante fallas y amenazas dinámicas."


## Diapositiva 4 — Hipótesis

**Tiempo sugerido: 1.5 min**

> "Entonces, ¿cómo resolvemos esto? Nuestra hipótesis parte de una idea simple: la resiliencia no se consigue con más drones, se consigue con **topología** — es decir, con cómo está diseñada la red de rutas."

**Explicar la hipótesis formal, desglosándola en partes (esto es lo más técnico de toda la presentación, hay que ir despacio):**

> "Modelamos el área de operación como un grafo geoespacial ponderado, G de V y E.
> 
> — Los **nodos** son puntos de despegue, relevo o vigilancia. — Las **aristas** son tramos de vuelo, y el costo de cada arista no es fijo: se calcula dinámicamente a partir de metadata real — elevación, vegetación, viento, temperatura, incendios activos, restricciones legales.
> 
> La hipótesis es que, si construimos ese grafo con **más de un camino factible** entre los puntos críticos, y aplicamos algoritmos de ruteo resiliente —rutas alternativas, caminos disjuntos, re-ruteo dinámico— entonces la flota puede mantener cobertura de vigilancia aunque falle un nodo o una arista específica. Y eso es justamente lo que el enfoque RSUPP, con su ruta única y estática, no puede hacer."

**Frase de cierre que conecta con el resto de la charla:**

> "De aquí en adelante, cada diapositiva construye una pieza de este grafo: cómo se compara con RSUPP, qué infraestructura necesita, de dónde sacamos los datos, y qué amenazas puede sufrir."

---

## Diapositivas 5–13 — Notas de apoyo (más breves)

### 5. Brecha y Mejora Propuesta

Usa la tabla comparativa como guion natural: recorre fila por fila — estructura, origen del riesgo, comportamiento ante una falla, contexto geográfico. Cierra con: _"En resumen: pasamos de un ciclo cerrado fijo a un grafo con caminos alternativos, alimentado con datos chilenos en tiempo real."_

### 6. Objetivos

Lee el objetivo general una sola vez, completo. Para los específicos, agrúpalos en tres ideas en vez de leer los 6 uno por uno: _(1) modelar y analizar la brecha con RSUPP, (2) integrar datos y detectar amenazas, (3) diseñar el ruteo resiliente y compararlo contra la línea base._

### 7. Infraestructura

Explica los tres tipos de nodo (base, relevo, vigilancia) con una analogía simple: _"la base es el aeropuerto, el relevo es una escala, y el nodo de vigilancia es el destino."_ Termina con la condición de k-conectividad — es el concepto técnico central de la diapositiva, di la frase completa: _"al menos dos caminos disjuntos entre cada nodo crítico y su base."_

### 8. Fuentes de Datos

No leas las seis fuentes una por una con el mismo tono — agrúpalas en dos frases: _"cuatro fuentes chilenas oficiales (OSM, IGM/MOP, DMC, CONAF) más dos fuentes de amenaza en tiempo real (FIRMS y MBN/Geoportal)."_ Menciona que cada una se accede por API o por descarga de capas geoespaciales.

### 9. Evidencia de Factibilidad

Diapositiva corta: solo enfatiza que **ya se hicieron consultas reales** a cada fuente (no es teórico) — eso responde de antemano cualquier pregunta de "¿y esto realmente se puede obtener?".

### 10. Metadata

Esta es la diapositiva más técnica después de la hipótesis. Explica la distinción estática/dinámica primero, y luego la fórmula de costo en palabras simples: _"el costo base depende de distancia, pendiente y riesgo; ese costo se multiplica por una penalización dinámica que, si hay un foco activo cerca, tiende a infinito — y ahí la arista simplemente se elimina del grafo."_

### 11. Amenazas

Menciona las cuatro categorías rápido (ambientales, operacionales, regulatorias, de infraestructura) con un ejemplo cada una, sin detenerte mucho — es una diapositiva de listado.

### 12. Conclusión y Próximos Pasos

Cierra con energía hacia el segundo informe: _"Con esta base ya podemos avanzar a instanciar el grafo sobre una zona piloto real, implementar la función de costo, y sobre todo, implementar y evaluar los algoritmos de ruteo resiliente comparados directamente contra RSUPP bajo fallas simuladas."_

### 13. Preguntas

Pausa, mira al público, y abre el espacio: _"Eso es todo de nuestra parte — quedamos atentos a sus preguntas."_

---

## Consejos generales de entrega

- **Las diapositivas 2 y 4 son las que más preguntas van a generar** (RSUPP y la fórmula de costo) — practícalas más que el resto.
- Evita leer las tarjetas/listas de la slide 8 y 11 palabra por palabra; agrúpalas en 2–3 frases como se sugiere arriba, o sonará mecánico.
- La diapositiva 5 (tabla comparativa) es un buen punto para hacer una pausa y preguntar al público si tienen dudas antes de seguir — marca el quiebre entre "el problema" y "la solución".



---


Hay una advertencia importante: en fuentes como OpenStreetMap y algunos servicios GIS, **no existe un conjunto único de campos fijo**; depende de la capa, del proveedor y de cómo esté publicada. Por eso distingo entre campos estructurales que se pueden esperar y campos que deben verificarse en la capa concreta antes de implementar.

## 1. OpenStreetMap / Geofabrik — edificios y obstáculos

### ¿Cómo se obtiene?

Para Chile pueden descargar un extracto de OpenStreetMap desde **Geofabrik**:

[https://download.geofabrik.de/south-america/chile.html](https://download.geofabrik.de/south-america/chile.html)

La descarga puede hacerse como:

- `.osm.pbf`
    
- Shapefile
    
- GeoPackage
    

Para su proyecto, **GeoPackage o PBF** son buenas opciones. Después pueden cargar la información en **QGIS o PostGIS**.

También pueden consultar OSM directamente mediante **Overpass API**, por ejemplo buscando objetos con:

```text
building=*
```

### ¿Qué datos/campos pueden encontrar?

En edificios, lo habitual es encontrar:

|Campo|Ejemplo|Utilidad|
|---|---|---|
|`osm_id`|`123456789`|Identificador|
|`building`|`residential`|Tipo de edificio|
|`name`|`Edificio A`|Nombre|
|`height`|`18`|Altura en metros, cuando existe|
|`building:levels`|`6`|Número de pisos|
|`addr:street`|`Av. Providencia`|Dirección|
|`addr:housenumber`|`123|Dirección|
|`geometry`|POLYGON|Huella del edificio|

### Ojo con algo importante

No todos los edificios tienen:

```text
height
building:levels
```

Por eso para **planificación de vuelo** yo no asumiría que la altura está disponible para todos.

La información que sí es mucho más consistente es:

```text
POLYGON + building
```

### ¿Sirve?

**Sí, muchísimo.**

La geometría del edificio puede convertirse en un obstáculo:

```text
POLYGON edificio
       ↓
buffer de seguridad
       ↓
zona no transitable
```

Y posteriormente:

```sql
ST_Intersects(arista, edificio_buffer)
```

permite detectar si una posible trayectoria pasa demasiado cerca.

**Valor para ustedes: 5/5.**

---

# 2. MINVU / Geoportal Chile — edificaciones

### ¿Cómo se obtiene?

A través del **Geoportal de Chile**, donde existen servicios GIS del MINVU, incluyendo servicios ArcGIS FeatureServer.

La capa que vimos:

**Construcciones en Nuevos Terrenos**

está publicada como servicio GIS.

### ¿Qué campos entrega?

Aquí depende de la capa concreta. En servicios FeatureServer normalmente encontrarán algo de este estilo:

|Campo|Utilidad|
|---|---|
|`OBJECTID`|Identificador|
|identificador de proyecto|Relacionar construcción|
|atributos de construcción|Características del elemento|
|información territorial|Clasificación/ubicación|
|`Shape`|Geometría|

Pero **no recomiendo asumir que tiene altura de edificios o número de pisos** sin revisar el esquema de esa capa específica.

### ¿Sirve?

Sí, pero yo la usaría como:

> **fuente oficial complementaria a OSM**

y no como fuente principal de obstáculos actuales.

**Valor: 3/5.**

---

# 3. MOP / IGM — geografía y elevación

### ¿Cómo se obtiene?

El MOP expone información cartográfica del IGM mediante servicios **ArcGIS REST MapServer**.

La fuente que vimos es:

```text
IGM50
```

y permite consultar sus capas directamente desde servicios GIS.

También pueden consumirlas desde QGIS usando:

```text
ArcGIS REST Server
```

### ¿Qué información pueden encontrar?

Entre las capas del servicio aparecen elementos relacionados con:

- curvas de nivel;
    
- hidrografía;
    
- vegetación;
    
- transporte;
    
- población;
    
- infraestructura;
    
- fisiografía.
    

Para el ruteo interesa especialmente la elevación.

### Campos

En una capa de curvas de nivel, conceptualmente tendrán algo como:

|Campo|Ejemplo|
|---|--:|
|identificador|1234|
|cota/elevación|250|
|tipo de curva|índice/intermedia|
|geometría|LINESTRING|

La geometría es importante porque posteriormente pueden interpolar la elevación.

### Mejor alternativa para el dron

Para ustedes sería incluso mejor trabajar con un **DEM (Digital Elevation Model)**.

En lugar de:

```text
curva 100 m
curva 110 m
curva 120 m
```

tener:

```text
lat     lon      elevation
-33.41  -70.61   845
-33.41  -70.60   851
...
```

y calcular:

Δh=hj−hi\Delta h = h_j-h_i

y luego:

pendienteij=Δhdijpendiente_{ij} = \frac{\Delta h}{d_{ij}}

### ¿Sirve?

**Sí, es fundamental.**

No solo para detectar terreno montañoso. También permite introducir una estimación de dificultad, consumo energético o restricción de vuelo.

**Valor: 5/5.**

---

# 4. Dirección Meteorológica de Chile — DMC

Esta es una de las fuentes que más me gusta para vuestro proyecto.

### ¿Cómo se obtiene?

La DMC publica servicios de datos meteorológicos mediante **JSON y GeoJSON**.

La documentación que revisamos incluye servicios para la red de estaciones meteorológicas y distintos productos meteorológicos.

Por ejemplo, conceptualmente:

```text
GET → servicio DMC
      ↓
JSON / GeoJSON
      ↓
PostGIS
```

### ¿Qué datos entrega?

Dependiendo del producto, pueden obtener variables como:

|Campo|Ejemplo|
|---|--:|
|estación|Quinta Normal|
|latitud|-33.44|
|longitud|-70.68|
|altitud|520|
|temperatura|31.2 °C|
|humedad relativa|24 %|
|viento|28 km/h|
|dirección del viento|230°|
|presión|1012 hPa|
|precipitación|0 mm|
|radiación|valor del producto|

La ventaja fundamental es que **la estación tiene ubicación geográfica**.

Por ejemplo:

```text
POINT(-70.68 -33.44)
```

### ¿Cómo lo usarían?

Pueden interpolar el valor meteorológico hacia los nodos de la red.

Por ejemplo:

```text
Estación DMC
      ↓
 temperatura = 32°C
 humedad = 22%
 viento = 30 km/h
      ↓
nodos cercanos
      ↓
aristas cercanas
```

Y generar:

```text
edge_AB.wind = 30
edge_AB.temperature = 32
edge_AB.humidity = 22
```

### ¿Sirve?

**Sí, muchísimo.**

Es exactamente el tipo de información que necesitan para un grafo dinámico.

**Valor: 5/5.**

---

# 5. DMC — condiciones de riesgo de incendios

Además de las estaciones, la DMC tiene productos relacionados específicamente con **condiciones meteorológicas asociadas al riesgo de incendios forestales**.

Esto es todavía más interesante.

En lugar de construir ustedes mismos:

```text
temperatura + humedad + viento
```

pueden disponer de productos que ya están orientados a la condición de riesgo.

### Datos relevantes

Según el producto pueden encontrarse variables como:

- temperatura;
    
- humedad;
    
- viento;
    
- condiciones extremas;
    
- indicadores asociados al riesgo.
    

### ¿Sirve?

**Sí, y puede ser una metadata de alto nivel.**

Por ejemplo:

```text
fire_weather_risk = HIGH
```

puede convertirse en:

```text
penalty_risk += 50
```

**Valor: 5/5.**

---

# 6. CONAF — vegetación y uso del suelo

### ¿Cómo se obtiene?

CONAF mantiene su **Catastro de Recursos Vegetacionales y Uso de la Tierra**, con información cartográfica georreferenciada.

Dependiendo de la región/capa pueden obtener información mediante sus plataformas y descargas GIS.

### ¿Qué información interesa?

Principalmente:

|Campo conceptual|Ejemplo|
|---|---|
|tipo de cobertura|bosque nativo|
|uso del suelo|forestal|
|tipo de vegetación|matorral|
|subtipo forestal|plantación|
|superficie|hectáreas|
|región|Valparaíso|
|geometría|POLYGON/MULTIPOLYGON|

La estructura exacta de atributos depende de la cobertura descargada.

### Este dato es fundamental

Porque un dron dedicado a incendios no debería considerar igual:

```text
bosque de alta combustibilidad
```

que:

```text
zona urbana
```

o:

```text
cuerpo de agua
```

Pueden crear una clasificación:

```text
Bosque nativo        → 1.0
Plantación forestal  → 0.9
Matorral             → 0.7
Agrícola             → 0.4
Urbano               → 0.1
Agua                 → restringido
```

### ¿Sirve?

**Sí, muchísimo.**

Especialmente porque es un **POLYGON**, que es exactamente el tipo de dato que pide vuestra tarea.

**Valor: 5/5.**

---

# 7. CONAF — riesgo de incendios

Otra fuente distinta dentro del ecosistema CONAF corresponde a información de:

- amenaza;
    
- riesgo;
    
- zonas de interfaz;
    
- riesgo territorial.
    

Esto es particularmente útil porque ya no hablamos solamente de:

> “qué tipo de terreno hay”.

Sino:

> “qué tan riesgosa es esta zona”.

### Datos

Conceptualmente:

|Campo|Ejemplo|
|---|---|
|nivel de amenaza|alto|
|nivel de riesgo|alto|
|zona de interfaz|sí|
|categoría|crítica|
|geometría|POLYGON|

La nomenclatura exacta dependerá de la cobertura descargada.

### ¿Sirve?

**Sí, probablemente es uno de los datasets más importantes del proyecto.**

**Valor: 5/5.**

---

# 8. NASA FIRMS — incendios activos

### ¿Cómo se obtiene?

NASA FIRMS tiene una **API específica** para consultar incendios activos.

Pueden solicitar los incendios de una región de Chile y recibirlos en formatos como CSV/JSON.

La API utiliza una clave (`MAP_KEY`).

Conceptualmente:

```text
API FIRMS
   ↓
Chile / bounding box
   ↓
incendios activos
   ↓
JSON/CSV
   ↓
PostGIS
```

### Campos

Esta fuente sí tiene un conjunto de campos bastante claro.

Entre los principales están:

|Campo|Ejemplo|Significado|
|---|--:|---|
|`latitude`|-33.420|Latitud|
|`longitude`|-70.820|Longitud|
|`brightness`|326.5|Brillo del pixel|
|`scan`|0.4|Tamaño/escaneo|
|`track`|0.5|Tamaño/escaneo|
|`acq_date`|2026-09-04|Fecha|
|`acq_time`|1530|Hora|
|`satellite`|NOAA-20|Satélite|
|`instrument`|VIIRS|Sensor|
|`confidence`|85|Confianza|
|`version`|...|Versión producto|
|`bright_t31`|...|Temperatura/brillo T31|
|`frp`|47.3|Fire Radiative Power|
|`daynight`|D|Día/noche|

### Este campo es especialmente interesante

```text
confidence
```

porque pueden evitar que una detección poco confiable tenga el mismo peso que una de alta confianza.

Por ejemplo:

```text
confidence = 90
       ↓
riesgo muy alto

confidence = 35
       ↓
riesgo menor
```

También:

```text
frp
```

puede utilizarse como medida relativa de intensidad radiativa.

### ¿Sirve?

**Sí, muchísimo.**

Es probablemente vuestra mejor metadata **dinámica** para detectar que una ruta se encuentra cerca de un posible incendio.

**Valor: 5/5.**

---

# 9. Geoportal Chile / MBN — áreas protegidas

### ¿Cómo se obtiene?

A través del **Geoportal de Chile**, que centraliza capas geográficas de diferentes organismos.

Para ustedes interesan especialmente:

- parques;
    
- reservas;
    
- monumentos naturales;
    
- bienes nacionales protegidos;
    
- otras áreas restringidas.
    

### Datos

Conceptualmente:

|Campo|Ejemplo|
|---|---|
|nombre|Parque Nacional X|
|categoría|Parque Nacional|
|organismo|CONAF/MBN|
|ID|identificador|
|superficie|hectáreas|
|geometría|POLYGON/MULTIPOLYGON|

La estructura exacta nuevamente depende de la capa.

### ¿Sirve?

Sí.

Permite crear:

```text
zona_restringida = true
```

y luego:

```text
si ST_Intersects(ruta, zona_restringida)
    ruta = NO DISPONIBLE
```

**Valor: 4/5.**

---

# 10. OpenStreetMap — caminos e infraestructura

No lo limitaría solamente a edificios.

De OSM también pueden obtener:

- carreteras;
    
- caminos;
    
- puentes;
    
- torres;
    
- líneas eléctricas;
    
- antenas;
    
- aeropuertos;
    
- infraestructura;
    
- cuerpos de agua;
    
- zonas urbanizadas.
    

### ¿Cómo?

Mediante el mismo PBF de Geofabrik o Overpass.

### ¿Para qué sirve?

Esto permite incorporar otras restricciones:

```text
aeropuerto
línea eléctrica
torre
puente
carretera
zona urbana
```

No todas tienen que ser zonas prohibidas, pero sí pueden funcionar como:

```text
obstacle
risk
landmark
restricted_area
```

---

# 11. Cómo quedarían unificados

La estructura que yo recomiendo para el proyecto sería:

```text
                    FUENTES
                       │
       ┌───────────────┼──────────────────┐
       │               │                  │
      OSM              DMC               CONAF
   edificios        clima              vegetación
   caminos          viento             riesgo
       │               │                  │
       └───────────────┼──────────────────┘
                       │
                    FIRMS
                 incendios activos
                       │
                       │
                 MOP / IGM
                  elevación
                       │
                       │
                Geoportal / MBN
               áreas restringidas
                       │
                       ▼
                ┌─────────────┐
                │   PostGIS   │
                └──────┬──────┘
                       │
                       ▼
                 GRAFO G=(V,E)
                       │
                       ▼
              MOTOR DE RUTEO
                       │
                       ▼
                     UAV
```

---

# 12. Lo realmente importante: qué termina llegando al grafo

No necesitan meter directamente los campos originales de cada fuente en el algoritmo.

Pueden transformar todo en atributos normalizados.

Por ejemplo:

### Nodo

```text
Nodo N23

latitude        = -33.421
longitude       = -70.731
elevation_m     = 845
temperature_C   = 31.8
humidity_pct    = 23
wind_kmh        = 27
fire_risk       = 0.82
active_fire     = false
restricted      = false
```

### Arista

```text
Arista N23 → N24

distance_m      = 1240
elevation_diff  = 38
slope_pct       = 3.06

building_risk   = 0
vegetation_risk = 0.83
weather_risk    = 0.61
fire_risk       = 0.72

active_fire_distance_m = 1850

status          = AVAILABLE
```

Y finalmente:

Cij=wdDij+wsSij+wvVij+wwWij+wfFij+woOijC_{ij} = w_dD_{ij} +w_sS_{ij} +w_vV_{ij} +w_wW_{ij} +w_fF_{ij} +w_oO_{ij}

donde pueden definir:

- DD: distancia;
    
- SS: pendiente;
    
- VV: vegetación;
    
- WW: meteorología;
    
- FF: incendio/riesgo;
    
- OO: obstáculos.
    

---

# 13. Qué fuentes sí mantendría

Después de revisar qué aporta cada una, mi selección para el proyecto quedaría así:

|Fuente|Dato principal|Geometría|Dinámico|Prioridad|
|---|---|---|---|---|
|**OSM/Geofabrik**|Edificios/obstáculos|POLYGON|No|⭐⭐⭐⭐⭐|
|**MOP/IGM**|Elevación/terreno|LINE/RASTER|No|⭐⭐⭐⭐⭐|
|**DMC**|Temperatura/humedad/viento|POINT|**Sí**|⭐⭐⭐⭐⭐|
|**CONAF**|Vegetación|POLYGON|No|⭐⭐⭐⭐⭐|
|**CONAF**|Riesgo incendio|POLYGON|Parcial|⭐⭐⭐⭐⭐|
|**NASA FIRMS**|Incendios activos|POINT|**Sí**|⭐⭐⭐⭐⭐|
|**MBN/Geoportal**|Restricciones|POLYGON|Poco|⭐⭐⭐⭐|
|**MINVU**|Construcciones|POLYGON|Poco|⭐⭐⭐|

## Para cumplir la rúbrica con el mínimo esfuerzo

Las **cuatro fuentes que no eliminaría** son:

**DMC → temperatura, humedad y viento**

**OSM → edificios y obstáculos**

**CONAF → vegetación/riesgo mediante polígonos**

**NASA FIRMS → incendios activos**

Y agregaría:

**MOP/IGM → elevación**

porque permite que el problema de ruteo tenga una dimensión física mucho más convincente.

La combinación da algo muy bueno para la segunda etapa:

Ruta oˊptima≠Ruta maˊs corta\boxed{\text{Ruta óptima} \neq \text{Ruta más corta}}

sino:

Ruta oˊptima=f(distancia, terreno, clima, obstaˊculos, riesgo e incendios)\boxed{\text{Ruta óptima}= f(\text{distancia, terreno, clima, obstáculos, riesgo e incendios})}

y cuando aparece un evento:

G(t0)→G(t1)G(t_0) \rightarrow G(t_1)

cambian los pesos o la disponibilidad de las aristas y el sistema puede buscar una ruta alternativa. Eso es justamente lo que les permite pasar desde un problema normal de planificación a **ruteo resiliente**.

Una limitación que conviene dejar explícita en el informe es que **ninguna de estas fuentes, por sí sola, entrega una “ruta de vuelo de dron” lista para usar**. Ustedes deben integrar las capas, normalizarlas y construir el grafo. Precisamente ahí está una parte importante del aporte ingenieril del proyecto.

Además, las fuentes de vuestro PDF base ya contemplan precisamente **OSM, IGM/MOP, DMC, CONAF, FIRMS y MBN/Geoportal Chile**, por lo que esta estructura profundiza y operacionaliza la selección que ya tenían.