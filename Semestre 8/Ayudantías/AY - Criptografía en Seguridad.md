# Ayudantía 2
27/08/25

## HASH
### Scrypt

Funcion de derivacion de claves que requiere mucha memoria además de tiempo de procesamiento. Similar a Bscrypt

### CRC (Cyclic Redundancy Check)

Codigo de detección de errores que NO es criptográficamente seguro

"Se entrega un flujo de datos igual a 10110011 y ponilomio generado en $x^4+x+1$. Obtén el CRC"

1. Pasamos el polinomio a bits: $x^4+x+1 = 10011$
2. Agregamos n cantidad de 0 al final del flujo, n = max potencia para verificar que el msje llegue bien
10110011*0000* 

3. XOR con el num binario obtenido del polinomio
10011 : 101100 11*0000* =  00101 (de izquierda a derecha)

nos queda 101 (ignorar los 0 a la izquierda), hay que bajar 2 bits a la derecha

10101 : 10011 , 11010 : 10011 y asi...

= 000*0100*

Por lo tanto, el flujo de datos enviado es 10110011*0100*
La integridad se vio comprometida dado que hay 1 bit encendido (debe se 0000 para que sea correcto)


### MD5 (Message Digest 5)

produce un hash de 128 bits 32 caracteres hexadecimal. Ya NO ES SEGURO 

EJ) mensaje "abc" y aplicar hash con MD5 (lo mas seguro esq no pregunten en ningun control esto)

1. Convertir el msje a bits
a: 01100001
b: 01100010
c: 01100011

01100001 01100010 01100011 *1*

512 bits - 64 bits para saber cuanto mensaje transmito y cuantos 0 hay.

### SHA
SHA256 (más común)

### Collision Attack

2 metodos de hash diferentes resultaron en un mismo resultado

