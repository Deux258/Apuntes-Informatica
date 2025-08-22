claudio.gonzalez4@mail.udp.cl
Claudio gonzalez p
# Clase 2
08/08/25
## Introducción a la Criptografía

*Ataque Dia 0:* Ataque creado específicamente para cierta entidad
*HASH* Identificación digital

###### Los primeros pasos de la Criptografía

- Nace de la necesidad de comunicar información confidencial. Eran rudimentarios pero ingeniosos, basados en sustituciones y transposiciones de símbolos.
- Desde Mesopotamia hasta China
- Jerogríficos no estandar, Propósito estético hasta el espionaje (tinta invisible)

###### Julio César y Cifrado de sustitución

Método débil en la actualidad que reemplaza el lenguaje por otro para cifrar mensajes
A -> D, B -> E.
Las letras sigue siendo igual de frecuente, solo que desplazado.

###### Innovaciones en la Edad Media y Renacimiento

- Cifrados polialfabéticos que superaban limitaciones del análisis de frecuencia
- Primeros tratados formales de criptografía

###### Cifrado de Vigenêre: La primera Clave Secreta

Usado por casi 3 siglos (desde XVI hasta XIX)
Clave secreta en forma de palabra o frase que se repetia sobre el mensaje.

###### Mary, Reina de Escocia y su Carta cifrada (1587)

Uso cifrado por sustitución para planear golpe contra la protestante Isabel I
Los criptógrafos de Isabel I lograron descifrar sus cartas (salió mal).

### Capítulo 3: Revolución Industrial y la Criptografía Mecánica

Mecanización para desarrollar cifrados más complejos que superaban las limitaciones manuales.
Factor decisivo en guerras modernas, siendo la base para la criptografía computacional.

Máquina de rotor de Hebern
Sentó las bases conceptuales, incrustando mensajes sin ser secuencial

###### La máquina Enigma y la Segunda guerra mundial

Ingeniero aleman en 1918: 3 t 4 rotores interconectados que cifraban el texto de forma extremadamente compleja semi-automática.
Descifrado por polacos y Reino Unido continuado por Alan Turing y su equipo. Logro crucial para acortar 2 años de guerra por los aliados


### Capítulo 4: La Era Digital y Criptografía Moderna

Transformación más radical por la capacidad de cálculo de las nuevas máquinas.

- Potencia Computacional
- Escala Global
- Fundamentos matemáticos (factorización de numeros primos)
- Seguridad demostrable

###### Criptografía en la era de computación

- Algoritmos matemáticos complejos 
	Métodos mecánicos reemplazados por algoritmos basados en problemas matemáticos computacionalmente difíciles para resistir ataques con ordenadores
- Principio de Kerchhoffs
	Seguridad debe resistir exclusivamente en la clave secreta, no en el secreto del algoritmo
 - Estándares globales
	DES, AES, RSA: base de la seguridad digital global


#### Criptografía Simétrica vs Asimétrica 

##### Simétrica
- Usa la misma clave para cifrar y descifrar
- **Desventaja** Distribución segura de claves

##### Asimétrica
- Clave de cifrado y descifrado distintas
- *Ventaja* Soluciona el problema de distribución de claves

Combinación de protocolos permite desarrollar comercio electrónico, banca en línea y comunicaciones privadas seguras a nivel global.

##### Internet y la criptografía: HTTPS y seguridad en línea

SSL/TLS y HTTPS
Cifrado de extremo a extremo. Se usa a veces para atacar estableciendo Comando Control para descifrar información.

Indicadores de ataque:
- Sitio web que apareció hace 7 días o menos

### Capítulo 5: Desafíos y Futuro de la Criptografía

Computación cuántica
- Equilibrio entre seguridad nacional y privacidad individual
- Más fácil romper el cifrado clásico
- *BlockChain* Mecanismo de seguridad distribuido
- Agencias como NIST están estandarizando algoritmos post-cuánticos para facilitar migración global antes de que quede la caga con los computadores cuánticos

La seguridad dependerá de nuestra capacidad para desarrollar soluciones criptográficas que se anticipen a estas amenazas mientras mantienen la usabilidad para usuarios no técnicos.


# Clase 3
12/08/25

## Criptografía Clásica

*Criptografía* Oculto - Escribir proveniente del griego Krypto - Grapho

### Proceso

.          K                   K
       |                    |
M --> *E* -->  C  --> *D* --> M

M: Mensaje de texto plano
C: Criptograma (texto cifrado)
*E*: Función de cifrado
K: Clave empleada para cifrar el texto en claro M
*D*: Función de descifrado

Las funciones criptográficas son funciones matemáticas
Los números que utilizan son numeros enteros, haciendo mas facil de procesar computacionalmente
$$ E_K(M) = C $$

##### Atbash
Método muy común de codificación del alfabeto hebreo. Método espejo
##### Morse
Representación de caracteres usando señales cortas y largas ( . ) y ( - ).

##### Cesar
Cifrado por desplazamiento. Cifrado por sustitución, técnica de codificación sencilla

##### ROT-13
Desplaza 13 veces el carácter

##### ROTx (base/2)
Buscar posición y desplazar x veces

EJ) A = 65
01000001
##### Vigenere
tabla grandote que relaciona mensaje, valor, letra(clave), valor (clave), suma, Mod 26 y letra cifrada
Mod 26 (sobrante de 26) los que son superiores se le resta (29 - 26 = 3).
Mensaje: lalapololeaconlalo
clave

##### Credenciales
Token: Permiso-Acceso a algún sitio

# Clase 4
19/08/25
## Password / Contraseña

Uno muchas veces autoriza ciertas cosas con letra chica

- Inseguridad en el Diseño
- Fallo en Criptografia
- Desconfiguracion en la nube
- Control de acceso roto

###### TOP 25 CWE 2024 (Most Dangerous Software Weaknesses)

- Impropia neutralizacion del input en generacion de pagina web
- Out-of-bounds Write
- Impropia neutralizacion de elementos especiales usados en querys SQL
- CSRF - Cross-site Request Forgery

##### Ataque Fuerza Bruta

1. Ataques a fuerza bruta Simples
2. Ataques con Diccionario
3. Ataques Hibridos
4. Ataques Reversa
5. Credential Stuffing

Hay mecanismos de contraataque como metodo de defensa

##### Servicios más atacados por fuerza bruta

1. RDP (Protocolo de Escritorio remoto)
2. SSH
3. VNC
4. Portales web
5. IMAP/POP3
6. Active Directory

¿Por cuanto tiempo es segura tu contraseña?

### Entropia

Cantidad de variacion de caracteres dentro de este
$$ H = L \space log_2(W)$$
W Base utilizada (cantidad caracteres que maneja)
L largo del string
NIST estima que un passcode deberia tener un minimo de 112 bits de entropia.

| Caracter Pool                    |                   | W caracteres       | Entropia por caracter | N caracteres minimo L |
| -------------------------------- | ----------------- | ------------------ | --------------------- | --------------------- |
| Digitos                          | $log_2 \space 10$ | 10 (0-9)           | 3.32 bits             | 34                    |
| letras chicas                    | $log_2 \space 26$ | 26 (a-z)           | 4.7 bits              | 24                    |
| letras y digitos                 |                   | 62 (A-Z, a-z, 0-9) | 5.95 bits             | 19                    |
| Todos los caracteres del teclado |                   | 94                 | 6.55 bits             | 18                    |

Recomendado usar 3 palabras simples aleatorias y sencillas de recordar

##### L8-Attacks

Usa la grabacion de video del reflejo de la pantalla de un dispositivo en la cornea del usuario (L8 = LATE, canto lateral del ojo)

##### Shoulder Surfing

Mirar por encima del hombro. Acto tradicional de sapear directamente la pantalla para robar información 


##### Keylohers

- Software Keyloggers
- Hardware Keyloggers

##### Man in the Middle

