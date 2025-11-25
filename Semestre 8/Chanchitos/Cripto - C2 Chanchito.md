# Cifrado asimétrico

Criptografía de llave pública. Usa un par de llaves, una publica y una privada. La llave publica se usa para cifrar los datos, la privada para descifrarlos. Esto permite asegurar la confidencialidad y autenticidad de la información.

*Tipos de algoritmos*
- Diffie y Hellman
- RSA
- DSA
- ECDSA
- EDDSA
### Logaritmo Discreto
Se denota matemáticamente como: 
$$x = Log_g(y) $$$$g^x=y$$
Fundamental en varios sistemas como Diffie y Hellman, DSA

### División Modular
Se expresa como:
$$x mod(y) = z$$
El cálculo debe retornar el resto de la división realizada, por ej $26 mod (3) =2$


## Diffie y Hellman

![[Pasted image 20251105201607.png]]
Permite el intercambio de claves que permite a dos partes generar una clave compartida secreta por un canal público inseguro.

Para este, se eligen dos números públicos, y cada interlocutor, un número secreto. Utilizando la fórmula matemática, cada interlocutor hace una serie de operaciones con los dos números públicos y su número secreto. Luego, ambos interlocutores se intercambian los resultados de forma pública.

### Tutorial
Supongamos que *Alice y Bob* quieren comunicarse a través de DH:
1. Se establecen un primo *p* y un generador *g*, ambos valores números enteros positivos.- Estos son públicos.
2. Alice escoge un valor *a* al azar y calcula $A = g^a mod(p)$ y envia *A* a Bob
3. Bob escoge al azar *b* y calcula $B = g^b mod(p)$ y envia *B* a Alice
4. A partir de estos valores, calculamos la clave compartida 
	- $s = B^a mod(p) = A^b mod(p)$

### Vulnerabilidades
Man in the Middle

### Dato
Tor utiliza Diffie Hellman

### Condiciones Necesarias

![[Pasted image 20251105220748.png]]

Para este tipo de ejercicios 
1. Ver si cumple condiciones necesarias
2. Si la llave privada cumple con $e \cdot d \cdot mod \space y(n) = 1$



# Cifrado Simétrico
Método criptográfico que usa una sola clave para cifrar y descifrar mensajes entre el emisor y receptor. Ambos mantienen en secreto esta clave, ya que con ella protegen los datos durante la transmision y garantizan su acceso en el proceso de descifrado.

- Cifrado por flujo
- Red de Feistel
- Cifrado por Bloque

## Cifrado por Flujo

*Ventajas*
- Eficiente para cifrar flujos de datos continuos, como en comunicaciones en tiempo real
- No requiere relleno, evita expansión del tamaño del cifrado
**Desventaja**
- Puede ser más vulnerable a ciertos tipos de ataques si la clave de flujo no se maneja bien
- Si se conoce la clave de flujo y texto cifrado, cagaste
- La seguridad depende en gran medida de la calidad del generador de clave de flujo

## Red de Feistel
Estructura que convierte mensaje en texto plano en cifrado de forma segura.
Permite que el proceso de cifrado y descifrado sea muy similar, simplificando su implementacion

### Funcionamiento
1. Se selecciona una cadena de 64 o 128 bits, dividiéndose en dos subcadenas, A y B de igual longitud N/2
2. Subclave: Se toma una función F, muy difícil de intervenir y una clave $K_i$
3. Se hacen una serie de operaciones complejas con $F$ y $K_i$ y con A o B.
	- El resultado se combina con la otra subcadena usando XOR
4. La cadena obtenida se cambia por la cadena con la que no se han realizado operaciones y se siguen haciendo las rondas.

![[Pasted image 20251105231929.png]]


## Cifrado por Bloque

![[Pasted image 20251105232003.png]]

Divide el texto plano en bloques de longitud fija, y cada bloque se cifra de forma inpendiente usando una clave secreta. Cada bloque tiene un tamaño específico.

### Funcionamiento
1. División del texto plano
	El texto se divide en bloques de tamaño específicos
2. Cifrado de bloques
	Cada bloque se cifra usando un algoritmo de cifrado y una clave secreta. Los bloques pueden cifrarse de manera independiente o encadenada.

*Ventajas*
- Alta seguridad, sobre todo con modos de operación adecuados
- Eficiencia en hardware y software
**Desventajas**
- Puede requerir padding
	Si el texto plano no es múltiple del tamaño del bloque
- Puede ser menos eficientes en aplicaciones que requieren cifrado de flujo continuo

Para encriptar mensajes cuya extensión supere el tamaño de un solo bloque, se usa *modo de operación*

### Métodos Modo de operación
- ECB
- CBC
- CTR
- Cipher feedback (CFB)
- Output Feedack (OFB)

#### ECB (Electronic Code-Book)
Divide el texto plano en bloques de igual tamaño y cifra cada bloque de forma independiente usando la misma clave

![[Pasted image 20251105232540.png]]
![[Pasted image 20251105232554.png]]


#### CBC (Cipher-Block Chaining)
Antes de ser cifrado, a cada bloque de texto se le aplica XOR con el bloque previo ya cifrado. Para inicializar se debe usar un vector de inicialización en el primer bloque

![[Pasted image 20251105232656.png]]

![[Pasted image 20251105232707.png]]


#### OFB (Output Feedback)
Se usa un vector de inicialización para crear un bloque pseudoaleatorio que se usa para realizar una operación XOR con el texto claro para generar el texto cifrado. Lo resultante es la entrada de la siguiente función, por lo que sólo depende del vector de inicialización y la llave.

![[Pasted image 20251105232859.png]]


## Algoritmos de Cifrado Simétrico

- DES
- 2DES
- 3DES
- AES
- Blowfish

### DES (Data Encription Standard)
Algoritmo obsoleto. Paso a ser muy inseguro por su vulnerabilidad a ataques de fuerza bruta. Durante los 80 y 90s, se usaba para proteger informacion de bancos, transacciones economicas y sistemas de comunicacion "seguros".

#### Funcionamiento
1. Un bloque de 64 bits se divide en dos mitades de 32 bits cada uno. Aparte, se tiene una clave de 56 bits más 8 de paridad.  
2. Expansión: A la mitad del bloque de 32 bits, se le hace una expansión a 48 bits mediante permutación de expansión. Esto con el propósito de realizar la mezcla con la subclave de 48 bits.  
3. Subclave: Se genera la subclave a partir de la clave entregada.  
4. Mezcla: Durante 16 rondas se realiza un XOR con la expansión y la subclave (ambas de 48 bits).  
5. Sustitución: El bloque expandido se divide ne 8 trazos de 6 bits. Cada uno de estos es procesado por las cajas de sustitución, la cual reemplaza los 6 bits de entrada por 4 bits de salida.  
6. Permutación: Las 32 salidas de las cajas de sustitución se reordenan según una permutación (esto permite que se cree una confusión).  

#### Vulnerabilidad
- Fuerza bruta
- Cripto-Análisis diferencial
- Cripto-Análisis lineal

#### ¿Cómo aumentar su seguridad?
Cifrando dos veces con una llave. Primero con $K_1$ y luego con $K_2$.


### 2DES (Double Data Encription Standard)
1. Se cifra con $K_1$
2. Se descifra con $K_2$
3. Se cifra nuevamente con $K_1$
$$EK (DK (EK (M)))$$
#### Vulnerabilidad
Ataque de cumpleaños

### 3DES (Trible Data Encription Standard)
Se diseña para mejorar la seguridad de DES y superar la vulnerabilidad de 2DES. 3DES es de los más rápidos para encriptar.

#### Funcionamiento
1. Se cifra con $K_1$: $EK_1(M)$
2. Se descifra con $K_2$: $DK_2 (EK_1(M))$
3. Se cifra nuevamente con $K_3$: $EK_3(DK_2(EK_1(M)))$

### AES (Advanced Encryption Standard)
Adoptado como estándar en 2001 para remplazar la DES. Usa cifrado por bloques.

- Longitud de la clave: 128, 192 o 256 bits
- Tamaño del bloque: 128 bits
- Rondas: 10, 12 o 14

#### Funcionamiento
Basado en sustitución-permutación que opera en una matriz de bytes llamada "estado". El número de rondas depende del tamaño de la clave.
- AES-128: 10 rondas  
- AES-192: 12 rondas 
- AES-256: 14 rondas

#### Etapas de cada Ronda
1. *SubBytes (Sust. de Bytes)*: Cada byte en la matriz de estado se reemplaza por otro byte usando una tabla de búsqueda llamada S-box.
2. *ShiftRows (Desplazamiento de filas)*: Se realiza un desplazamiento cíclico de las filas de la matriz de estado.
3. *MixColumns (Mezcla de columnas)*: Las columnas de la matriz de estado se mezclan usando operaciones matemáticas en un campo finito.
4. *AddRoundKey (aadición de Clave de Ronda)*: Se realiza una operación XOR entre la matriz de estado y una subclave derivada de la clave principal.

### BlowFish
Desarrollado como alternativa a DES, ofreciendo mayor seguridad y flexibilidad.

- Bloque fijo de 64 bits
- Tamaño clave variable de 32 a 448 bits.

#### Funcionamiento
Estaba basada en una red de Feistel que consta de 16 rondas. En una red de Feistel, el texto plano se dibide en dos mitades que se procesan en cada ronda.

## Tipos de Padding

- PKCS#5  
- PKCS#7  
- ISO/IEC 7816-4  
- ZEROES PADDING  
- SPACE PADDING  
- ANSI X9.23  
- ISO 10126

### PKCS#5

Bloques de 8 bytes (64 bits). Al final del mensaje se le agrega el valor del padding, por ejemplo:

*Mensaje* "hello" (5 bytes)
8 bytes - 5 bytes = 3 bytes
*Padding* 0x03
*Mensaje con Padding* = 0x48656C6CF \ 03 \ 03 \ 03

### PKCS#7
Para cifrados de bloques que usan hasta 255 bytes. misma lógica que PKCS#5

EJ) Para un bloque de 16 bytes  
Mensaje: “hello” (5 bytes)  
Cálculo: 16 bytes - 5 bytes = 11 bytes = 0x0B 
Mensaje con padding: 0x48656C6C6F\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B\x0B\

### ISO/IEC 7819-4
Es para cifrados de bloque de cualquier tamaño que sea multiplo del tamaño del bloque
Se agrega 0x80 al final del mensaje, luego 0x00 hasta completar el tamaño de este

EJ) Para un bloque de 16 bytes  
Mensaje: “hola” (4 bytes)  
Padding necesario: 12 bytes  
Mensaje con padding: 0x686F6C61\ *x80*\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\


### ZERO PADDING 
Todos los bytes que sean requeridos se rellenan con un padding de 0. NO ha sido estandarizado para encriptacion.
**PROBLEMA**: Es que no puede ser reversible si el archivo original termina con uno o más bytes cero, siendo imposible de distinguir entre 0 de datos y 0 de padding

EJ) Para un bloque de 8 bytes  
Mensaje: “Hello” (5 bytes)  
Padding necesario: 3 bytes  
Mensaje con padding: 0x48656C6C6F\ *x00\x00\x00*\


### SPACE PADDING
Rellena con espacios en blancos 0x20 en ASCII

Para un bloque de 8 bytes  
Mensaje: “Hello” (5 bytes)  
Padding necesario: 3 bytes  
Mensaje con padding: 0x48656C6C6F\ *x20\x20\x20*\ (“Hello “)

### ANSI X9.23 (Estándar Estadounidense)
Agrega todos ceros excepto el último byte que indica la cantidad total de bytes de padding.

Para un bloque de 8 bytes  
Mensaje: “Hello” (5 bytes)  
Padding necesario: 3 bytes  
Mensaje con padding: 0x48656C6C6F\x00\x00\ *x03* \

### ISO 10126 (Internacional)
Este padding incluye valores aleatorios excepto el último byte, que indica cuántos bytes fueron agregados como padding.

Para un bloque de 8 bytes  
Mensaje: “Hello” (5 bytes)  
Padding necesario: 3 bytes  = 0x03
Mensaje con padding: 0x48656C6C6F\xYY\xYY\x03\


# Números de Fermat
Se usa como exponente publico eficiente y seguro

$$F_n = 2^{2^n} + 1$$
Donde $n$ es un numero entero no negativo

*Primeros números de Fermat*
- F0​=$2^{2^0}+1=2^1+1=3$
- F1=$2^{2^1}+1=2^2+1=5$
- F2=$2^{2^2}+1=2^4+1=17$
- F3=$2^{2^3}+1=2^8+1=257$
- F4=$2^{2^4}+1=2^{16}+1=65537$

1. *Crecimiento extremadamente rápido*, crecen de forma doble-exponencial
2. *Relación con números primos*: Fermat conjeturo que todos eran primos, pero Euler demostró que $F_5$ es compuesto
3. *Forma binaria*: Todos terminan en dígito 7 en decimal
4. *Relación con construcciones geométricas*: Gauss demostró que un polígono regular de $n$ lados es construible con regla y compas si $n$ es producto de una potencia de 2 y primos de Fermat distintos.

### Ejemplo
Generación de numeros primos para criptografia RSA

Los numeros de Fermat, especificamente $F_4 = 65537$ se usan para: Exponente público.

- Es un numero primo grande
- Permite computacion eficiente por operaciones de desplazamiento
- Tiene solo dos bits en 1 en su representacion binaria
- Buen balance entre seguridad y eficiencia computacional

### Número de Fernat más usado en criptografía actual
$F_4 = 65537$

Es por su eficiencia computacional, balance seguridad-rendimiento, amplia adopción (protocolos TLS/SSL) y ser primo, tamaño optimo para evitar vulnerabilidades asociadas con exponentes muy pequeños.

Los números mayores no se usan porque son compuestos y demasiados grandes para aplicaciones prácticas.


# Firmas Digitales

![[Pasted image 20251106220146.png]]


	