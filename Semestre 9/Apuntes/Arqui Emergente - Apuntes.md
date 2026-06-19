
El Coordinador de TI centraliza la totalidad de las decisiones técnicas y la priorización de proyectos. Si bien esto otorga agilidad inmediata, de cara a la expansión internacional proyectada a mercados de alta complejidad logística (como Brasil, Perú y Colombia), este esquema autocrático se transformará en un punto de falla organizacional.



1. **¿Qué significa que REST sea un 'estilo arquitectónico' y no un protocolo, y cuál es su relación con HTTP y CoAP?**
    

- [ ] REST es un estilo que define los algoritmos de cifrado que deben usar los protocolos de la capa de transporte.
- [ ] REST es un protocolo de capa de red que permite la comunicación entre dispositivos IoT sin necesidad de IP.
- [ ] REST es un conjunto de principios de diseño para sistemas distribuidos (definido por Fielding en 2000); HTTP y CoAP son protocolos que implementan esos principios, haciendo que las aplicaciones que los usan correctamente sean RESTful.
- [ ] Ninguna de las demás respuestas.

R: Es un estilo arquitectónico. HYYP y CoAP se encargan de dar soporte a estas restricciones


2. **¿Cuál es la principal ventaja de las tecnologías LPWAN (LoRaWAN, Sigfox, NB-IoT) respecto a IEEE 802.15.4 en despliegues a escala de ciudad?**
    

- [x] LPWAN sacrifica tasa de datos a cambio de alcances de kilómetros y consumo mínimo, complementando a IEEE 802.15.4 en escenarios donde los sensores están dispersos en grandes áreas.
- [ ] LPWAN usa topologías mesh que garantizan conectividad redundante en ciudades con alta densidad de edificios.
- [ ] Ninguna de las demás respuestas.    
- [ ] LPWAN ofrece mayor tasa de datos que IEEE 802.15.4, lo que permite transmitir video en tiempo real desde sensores remotos.

IEEE 80.2.15.4 pensado para redes de área personal (WPAN)
LPWAN cubren a escala metropolitana con bajisimo consumo energético. reduce ancho de banda a cambio de largo alcance



3. **¿Qué distinción existe entre un dispositivo FFD y un RFD en IEEE 802.15.4, y cómo afecta a la topología de la red?**
    

- [ ] Ninguna de las demás respuestas.
- [ ] Los FFD tienen mayor consumo de energía pero mayor seguridad gracias al cifrado AES-256.
- [ ] Los FFD usan la banda de 5 GHz mientras que los RFD operan en 2.4 GHz para evitar interferencias.
- [x] Los FFD pueden actuar como coordinadores PAN, routers o dispositivos finales y comunicarse con cualquier otro; los RFD solo realizan tareas simples y solo se comunican con un FFD.

FFD (Full Function Devices) implementan todas las funciones del estándar y pueden enrutar tráfico. Los RFD (Reduced Function Devices) lo mismo pero con recursos muy limitados


4. **¿Por qué el uso de NAT (Network Address Translation) es considerado un 'anti-patrón' en el contexto del IoT?**
    
- [ ] Ninguna de las demás respuestas.
- [ ] Porque NAT aumenta el tamaño de las tramas Ethernet y genera overhead. 
- [x] Porque NAT rompe la conectividad extremo a extremo, impidiendo que los dispositivos IoT sean directamente accesibles desde Internet.
- [ ] Porque NAT solo funciona con IPv6 y no es compatible con los dispositivos IoT actuales.

Uno de los pilares de internet es que cualquier nodo pueda comunicarse bidireccionalmente con otro. NAT enmascara multiples dispositivos tras una sola IP publica, impidiendo que un server externo inicie conexion directa sin tecnicas complejas de tunelizacion


5. **¿Por qué la fragmentación de paquetes IPv6 supone un problema especial en redes IoT basadas en IEEE 802.15.4?**
    

- [ ] Porque IPv6 no soporta fragmentación, lo que imposibilita su uso sobre 802.15.4.
- [ ] Ninguna de las demás respuestas.
- [ ] Porque la fragmentación en IPv6 es procesada por todos los routers intermedios, generando cuellos de botella.
- [x] Porque en IPv6 solo el origen puede fragmentar, y el MTU mínimo de 1280 bytes es mucho mayor que los 127 bytes de la trama 802.15.4.

IPv6 obliga a que cualquier enlace soporte al menos 1280 bytes y prohibe la fragmentacion en routers intermedios (solo emisor).
IEEE 802.15.4 sólo admite 127 byes

6. **¿Cuál es la diferencia más importante entre los requisitos de tiempo real en el IIoT industrial versus el IoT de consumo?**
    

- [ ] El IIoT prioriza el ancho de banda sobre la latencia, mientras que el IoT de consumo prioriza la latencia.
- [ ] El IIoT solo funciona con protocolos propietarios porque los estándares abiertos no cumplen sus requisitos de seguridad.
- [ ] Ninguna de las demás respuestas.
- [x] El IIoT requiere latencias submilisegundo para control de procesos, mientras que en el IoT de consumo 'tiempo real' puede significar varios segundos.
    

7. **¿Cuál es la diferencia fundamental entre el modelo Request/Response y el modelo Publish/Subscribe en términos de acoplamiento y adecuación al IoT?**
    

- [x] En Request/Response el cliente debe conocer al servidor y este debe estar activo; en Pub/Sub los publicadores y suscriptores no se conocen entre sí y el broker desacopla espacio, tiempo y sincronización.
- [ ] Ninguna de las demás respuestas.
- [ ] Request/Response es asíncrono y desacoplado, mientras que Pub/Sub es síncrono y requiere que cliente y servidor estén activos al mismo tiempo.
- [ ] Pub/Sub siempre es más eficiente que Request/Response porque usa UDP en lugar de TCP.
    

8. **¿Por qué los mensajes multicast en CoAP deben ser siempre del tipo NON (Non-confirmable)?**
    

- [ ] Porque la norma RFC 7390 prohíbe el cifrado DTLS en mensajes CON enviados a grupos multicast.
- [ ] Porque los mensajes multicast CoAP se envían sobre TCP y NON es el único tipo compatible con ese transporte.
- [x] Porque no es posible recibir un ACK de un grupo de destinatarios, lo que hace imposible implementar fiabilidad CON en una comunicación multicast.
- [ ] Ninguna de las demás respuestas.
    

9. **¿Qué son los gemelos digitales (Digital Twins) y cómo se relacionan con el IoT industrial?**
    

- [ ] Los gemelos digitales son copias físicas de los equipos industriales que se usan para pruebas sin riesgo de dañar el equipo original.
- [ ] Los gemelos digitales son modelos 3D estáticos de las instalaciones industriales usados para planificación del mantenimiento.
- [ ] Ninguna de las demás respuestas.
- [x] Un gemelo digital es una representación digital en tiempo real de un activo físico, alimentada continuamente por datos de sensores IoT, que permite simulación, predicción de fallos y optimización sin intervenir el equipo real.
    

10. **¿Por qué la convergencia IT/OT en el IIoT crea nuevas vulnerabilidades de ciberseguridad que no existían en los sistemas OT tradicionales aislados?**
    

- [ ] Porque los sistemas IT modifcan el firmware de los PLCs automáticamente, introduciendo errores no intencionados.
- [ ] Porque los protocolos IT como HTTP no pueden comunicarse con los PLCs, generando errores de traducción que los atacantes aprovechan.
- [x] Porque los sistemas OT fueron diseñados para redes físicamente aisladas sin seguridad cibernética; al conectarlos a redes IP y a Internet, su enorme superficie de ataque queda expuesta.
- [ ] Ninguna de las demás respuestas.
    

11. **¿Cuál es el principio fundamental que hizo exitoso el diseño de red abierta (open-architecture networking) de Internet?**
    

- [ ] IP proporciona control de flujo y recuperación de pérdidas extremo a extremo.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] La separación en capas permite que cada tecnología evolucione independientemente sin afectar a las demás.
    
- [ ] El control centralizado de la red garantiza la calidad del servicio.
    

12. **¿Cuál es el problema fundamental que resuelve 6LoWPAN, y por qué no es posible simplemente transmitir IPv6 directamente sobre IEEE 802.15.4?**
    

- [ ] IPv6 requiere un MTU mínimo de 1280 bytes, mientras que la trama 802.15.4 tiene solo 127 bytes; 6LoWPAN actúa como capa de adaptación con compresión de cabecera y fragmentación.
    
- [ ] IEEE 802.15.4 usa direccionamiento MAC de 64 bits incompatible con las direcciones IPv6 de 128 bits.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] IPv6 no soporta multicast sobre redes inalámbricas, lo que hace imposible su uso directo sobre 802.15.4.
    

13. **¿Por qué TCP es inadecuado para dispositivos IoT de baja potencia (Clase 0 y Clase 1)?**
    

- [ ] Porque TCP no soporta direcciones IPv6 y los dispositivos IoT requieren IPv6 para operar.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] Porque TCP solo funciona en redes cableadas y no es compatible con IEEE 802.15.4.
    
- [ ] Porque TCP interpreta las pérdidas de radio como congestión y reduce su ventana de transmisión, colapsando el rendimiento en redes IoT con alta tasa de pérdidas naturales.
    

14. **¿Cuál es la razón fundamental por la que los estándares de enlace IoT (como IEEE 802.15.4) sacrifican tasa de datos frente a tecnologías como Wi-Fi o Ethernet?**
    

- [ ] Porque el IoT prioriza minimizar el consumo de energía para lograr años de vida útil en batería, aunque esto implique tasas de datos bajas y tramas pequeñas.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] Porque los dispositivos IoT no necesitan transmitir datos, solo recibir comandos del servidor.
    
- [ ] Porque el estándar IEEE 802.15.4 fue diseñado exclusivamente para redes industriales que requieren baja latencia.
    

15. **¿Qué ventaja ofrece UDP sobre TCP en el contexto de dispositivos IoT con duty cycling?**
    

- [ ] UDP comprime automáticamente los datos del payload, reduciendo el consumo de energía.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] UDP garantiza la entrega de paquetes con mayor fiabilidad que TCP gracias a su checksum obligatorio.
    
- [ ] UDP es sin conexión y sin estado, lo que lo hace compatible con dispositivos que se duermen entre transmisiones y no pueden mantener conexiones activas.
    

16. **¿Por qué las soluciones verticales (silos cerrados) no son la arquitectura de referencia adecuada para un IoT escalable?**
    

- [ ] Porque los protocolos usados en soluciones verticales (MQTT, HTTP) no están estandarizados por organismos internacionales.
    
- [ ] Porque las soluciones verticales son demasiado costosas de implementar para fabricantes pequeños y medianos.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] Porque generan silos de datos sin interoperabilidad entre fabricantes, dependen de la disponibilidad de la nube, y tienen problemas de escalabilidad y evolución cuando los dispositivos codifican endpoints fijos del servidor.
    

17. **¿Cuál es la principal limitación del modelo Pub/Sub respecto a la evolución del sistema a largo plazo?**
    

- [ ] La estructura de los mensajes es implícito y no hay negociación de formato; si el publicador cambia la estructura del payload, los suscriptores se rompen sin notificación automática.
    
- [ ] El modelo Pub/Sub no escala porque el broker es un componente centralizado que no puede replicarse.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] El modelo Pub/Sub no permite usar TLS para cifrar las comunicaciones entre publicadores y el broker.
    

18. **¿Por qué el principio 'menos datos = menos fragmentos = menor consumo de energía' es crítico en el diseño de protocolos IoT sobre 6LoWPAN?**
    

- [ ] Porque cada fragmento adicional implica más transmisiones de radio, que es el componente que más energía consume; si un fragmento se pierde hay que retransmitir todo el paquete.
    
- [ ] Porque la fragmentación en 6LoWPAN está limitada a un máximo de 2 fragmentos por paquete IPv6.
    
- [ ] Porque cada fragmento 6LoWPAN consume el doble de energía que una trama completa debido al procesamiento AES.
    
- [ ] Ninguna de las demás respuestas.
    

19. **¿Qué aporta TSN (Time-Sensitive Networking) al IIoT que el Ethernet estándar no puede ofrecer?**
    

- [ ] TSN reemplaza completamente a Ethernet con un nuevo estándar que garantiza velocidades de 400 Gbps en entornos industriales.
    
- [ ] TSN cifra el tráfico Ethernet con AES-256 para proteger las comunicaciones industriales de ataques man-in-the-middle.
    
- [ ] TSN añade determinismo temporal a Ethernet estándar, proporcionando latencias acotadas y predecibles, sincronización de tiempo precisa y reserva de ancho de banda para tráfico crítico, permitiendo coexistir tráfico de control y diagnóstico.
    
- [ ] Ninguna de las demás respuestas.
    

20. **¿Qué diferencia fundamental existe entre CSMA/CD (usado en Ethernet) y CSMA/CA (usado en Wi-Fi) respecto al manejo de colisiones?**
    

- [ ] CSMA/CA es más lento porque requiere un servidor central que coordine el acceso al medio.
    
- [ ] CSMA/CD usa cifrado AES para prevenir colisiones, mientras que CSMA/CA no.
    
- [ ] CSMA/CD detecta colisiones mientras transmite y reacciona; CSMA/CA intenta evitar las colisiones antes de transmitir.
    
- [ ] Ninguna de las demás respuestas.
    

21. **¿Qué relación existe entre los protocolos tradicionales (HTTP, AMQP, SIP) y sus equivalentes IoT (CoAP, MQTT, CoSIP)?**
    

- [ ] Los protocolos IoT son versiones encriptadas de los protocolos tradicionales diseñadas para redes inalámbricas.
    
- [ ] Los protocolos IoT son protocolos completamente nuevos sin relación semántica con los tradicionales.
    
- [ ] Los protocolos IoT replican la misma semántica de los tradicionales pero usando formatos binarios compactos sobre UDP, reduciendo el overhead en un factor de 10x-100x.
    
- [ ] Ninguna de las demás respuestas.
    

22. **¿Cuál es la razón principal por la que IPv6 es considerada la única solución sostenible para el IoT a largo plazo?**
    

- [ ] IPv6 es más rápido que IPv4 gracias a su cabecera variable que se adapta a dispositivos restringidos.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] IPv6 elimina la necesidad de routers en la red IoT gracias a su mecanismo de multicast.
    
- [ ] IPv6 ofrece un espacio de 2^128 direcciones y conectividad extremo a extremo sin NAT, suficiente para billones de dispositivos IoT durante siglos.
    

23. **¿Por qué la diferencia entre un 'recurso' REST y su 'representación' es conceptualmente importante en el diseño de APIs IoT?**
    

- [ ] Porque el recurso se almacena en la base de datos y la representación en el sistema de archivos; son componentes separados del servidor.
    
- [ ] Porque un recurso es la entidad lógica (p.ej. la temperatura de un sensor), mientras que su representación es una vista de su estado en un momento dado (p.ej. en JSON, CBOR o texto plano); el mismo recurso puede tener múltiples representaciones negociables.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] Porque la representación contiene el código del recurso, y el servidor la ejecuta para obtener el valor actual del sensor.
    

24. **En CoAP, ¿cuál es la diferencia conceptual entre el campo Message-ID y el campo Token, y por qué se dice que son 'ortogonales'?**
    

- [ ] Ninguna de las demás respuestas.
    
- [ ] Message-ID sirve para deduplicación y fiabilidad de mensajes individuales; Token empareja peticiones con respuestas aunque lleguen en mensajes con distinto Message-ID. Son ortogonales porque cumplen funciones independientes.
    
- [ ] Message-ID identifica el recurso solicitado y Token identifica al cliente; son ortogonales porque cada cliente tiene un único token.
    
- [ ] Message-ID y Token son lo mismo, pero Message-ID se usa en mensajes CON y Token en mensajes NON.
    

25. **¿Qué rol cumple RPL (Routing Protocol for Low-Power and Lossy Networks) en el stack IoT, y cómo difiere de protocolos como OSPF?**
    

- [ ] RPL es equivalente a OSPF pero opera en la capa de enlace, mientras que OSPF opera en la capa de red.
    
- [ ] RPL reemplaza a IPv6 en redes IoT porque OSPF ya implementa las funciones de enrutamiento necesarias.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] RPL está diseñado para redes con batería y pérdidas, usa el algoritmo Trickle para minimizar overhead de control, y construye un DAG orientado a la raíz optimizando métricas como energía residual y ETX.
    

26. **¿Por qué BLE (Bluetooth Low Energy) tiene mayor adopción que ZigBee en dispositivos de consumo, aunque ambos tengan bajo consumo?**
    

- [ ] BLE tiene mayor alcance que ZigBee, lo que lo hace más adecuado para redes de área amplia.
    
- [ ] BLE está disponible en prácticamente todos los smartphones actuales, lo que facilita la integración directa con dispositivos de consumo sin necesidad de gateways adicionales.
    
- [ ] BLE soporta redes mesh con hasta 65.000 nodos, mientras que ZigBee se limita a topologías estrella.
    
- [ ] Ninguna de las demás respuestas.
    

27. **¿Cuál es la principal ventaja de SLAAC (Stateless Address Autoconfiguration) para el despliegue masivo de dispositivos IoT?**
    

- [ ] Proporciona mayor seguridad que DHCP al cifrar las direcciones IP asignadas.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] Reduce el tamaño de la cabecera IPv6 de 40 bytes a menos de 10 bytes.
    
- [ ] Permite a los dispositivos generar su propia dirección IPv6 global automáticamente al conectarse, sin intervención humana ni servidor DHCP.
    

28. **¿Cuál es el propósito del mecanismo Last Will and Testament (LWT) en MQTT, y qué tipo de evento lo dispara?**
    

- [ ] El LWT es un mecanismo de herencia de suscripciones que transfiere los topics de un cliente desconectado a otro cliente activo.
    
- [ ] El LWT es un mensaje que el cliente envía voluntariamente al desconectarse de forma limpia para notificar a los demás su estado final.
    
- [ ] El LWT es un mensaje configurado al conectar que el broker publica automáticamente si detecta que el cliente se desconecta de forma inesperada (timeout keepalive o error TCP), sin haber enviado DISCONNECT.
    
- [ ] Ninguna de las demás respuestas.
    

29. **¿Cuál es el principio de diseño de TSCH (Time Slotted Channel Hopping) en IEEE 802.15.4e para entornos industriales?**
    

- [ ] Ninguna de las demás respuestas.
    
- [ ] TSCH aumenta la tasa de datos combinando múltiples canales en paralelo mediante OFDM.
    
- [ ] TSCH combina TDMA sincronizado con salto de canal entre ranuras temporales, logrando alta fiabilidad y determinismo en entornos industriales ruidosos.
    
- [ ] TSCH elimina la necesidad de sincronización de tiempo al usar frecuencias spread-spectrum de banda ultra-ancha.
    

30. **¿Cuál es la característica más importante del protocolo HTTP que lo hace inadecuado directamente para dispositivos IoT restringidos?**
    

- [ ] HTTP usa cabeceras de texto de cientos de bytes, requiere TCP con handshake, y no soporta multicast ni observación nativa de recursos.
    
- [ ] Ninguna de las demás respuestas.
    
- [ ] HTTP no puede comunicarse con servidores en IPv6, lo que limita su uso en el IoT.
    
- [ ] HTTP no tiene soporte para autenticación, lo que hace imposible usarlo de forma segura en IoT.