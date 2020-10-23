<a href="https://cooltext.com"><img src="https://images.cooltext.com/5474519.gif" width="346" height="89" alt="Resumen" /></a>
<br />Image by <a href="https://cooltext.com">Cool Text: Free Logos and Buttons</a> - <a href="https://cooltext.com/Edit-Logo?LogoID=3663540622">Create An Image Just Like This</a>

**1.1.1. Características generales de la arquitectura ARM**
ARM es una arquitectura RISC (Reduced Instruction Set Computer) de 32 bits, excepto la versión del core ARMv8-A que es mixta 32/64 bits (bus de 32 bits con registros de 64 bits). Se trata de una arquitectura licenciable, quiere decir que la empresa desarrolladora ARM Holdings diseña la arquitectura, pero son otras compañías las que fabrican y venden los chips,
llevándose ARM Holdings un pequeño porcentaje por la licencia.<br>
El chip en concreto que lleva la Raspberry Pi es el BCM2835, se trata de un SoC (System on a Chip) que contiene además de la CPU otros elementos como un núcleo GPU y un núcleo DSP (Digital signal processing) que es un procesador más pequeño y simple que el principal, pero especializado en el procesado y representación de señales analógicas.<BR>
**Registros**<br>
La arquitectura ARMv6 presenta un conjunto de 17 registros (16 principales más uno de estado) de 32 bits cada uno.<br>
**Registros Generales.** Su función es el almacenamiento temporal de datos.<br>
**Registros Especiales.** Son los últimos 3 registros principales: R13, R14 y R15.<br>
**Registros CPSR.** Almacena las banderas condicionales y los bits de control.<br>

**1.1.2.** El lenguaje ensamblador<br>
El ensamblador es un lenguaje de bajo nivel que permite un control directo de la CPU y todos los elementos asociados. Desarrollar programas en lenguaje ensamblador es un proceso laborioso. El procedimiento es similar al de cualquier lenguaje compilado. Un conjunto de instrucciones y/o datos forman un módulo fuente. Este módulo es la entrada del compilador, que chequea la sintaxis y lo traduce a código máquina formando un módulo objeto. Finalmente, un enlazador (montador ó linker) traduce todas las referencias relativas a direcciones absolutas y termina generando el ejecutable.<br>
Generalmente, y dado que crear programas un poco extensos es laborioso, el ensamblador se utiliza como apoyo a otros lenguajes de alto nivel para 3 tipos de situaciones:*<br> - Operaciones que se repitan un número elevado de veces.<br> - Cuando se requiera una gran velocidad de proceso. <br>- Para utilización y aprovechamiento de dispositivos y recursos del sistema.*<br>

**1.1.3** El entorno<br>
Los pasos habituales para hacer un programa (en cualquier lenguaje) son los siguientes: lo primero es escribir el programa en el lenguaje fuente mediante un editor de programas. El resultado es un fichero en un lenguaje que puede entender el usuario, pero no la máquina. Para traducirlo a lenguaje máquina hay que utilizar un programa traductor. Éste genera un fichero con la traducción de dicho programa, pero todavía no es un programa ejecutable. Un fichero ejecutable contiene el programa traducido más una serie de códigos que debe tener todo programa que vaya a ser ejecutado en una máquina determinada. Entre estos códigos comunes se encuentran las librerías del lenguaje. El encargado de unir el código del programa con el código de estas librerías es un programa llamado montador (linker) que genera el programa ejecutable.<br>
Durante el proceso de creación de un programa se suelen producir errores. Hay dos tipos de errores: los sintácticos o detectables en tiempo de traducción y los errores semánticos o detectables en tiempo de ejecución. Los errores sintácticos son, por ejemplo, escribir mal una instrucción o hacer una operación entre dos tipos de datos incompatibles. Estos errores son detectados por el traductor y se deben solucionar para poder generar un ejecutable.<br>
Una vez que se tiene un programa sintácticamente correcto lo podemos ejecutar, pero ésto no implica que el programa sea correcto. Todas las instrucciones pueden ser correctas, pero se puede haber olvidado poner la condición de salida de un bucle (y que no termine nunca) o que sencillamente el programa no haga lo que queremos.<br>
**1.1.5** Aspecto de un programa en ensamblador<br>
La principal característica de un módulo fuente en ensamblador es que existe una clara separación entre las instrucciones y los datos. La estructura general mas comun es:<br>
***Sección de datos.*** Viene identificada por la directiva .data. En esta zona se definen todas las variables que utiliza el programa con el objeto de reservar memoria para contener los valores asignados.<br>
***Sección de código.*** Se indica con la directiva .text, y sólo puede contener código o datos no modificables.<br>
Un módulo fuente, está formado por instrucciones, datos, símbolos y directivas. Las instrucciones son representaciones nemotécnicas del juego de instrucciones del procesador.<br>
**Datos**
Un dato es una entidad que aporta un valor numérico, que puede expresarse en distintas bases o incluso a través de una cadena. Los símbolos son representaciones abstractas que el ensamblador maneja en tiempo de ensamblado pero que en el código binario resultante tendrá un valor numérico concreto. Hay tres tipos de símbolos: las etiquetas, las macros y las constantes simbólicas. Los datos se pueden representar de distintas maneras. Para representar números tenemos 4 bases. La más habitual es en su forma decimal, la cual no lleva ningún delimitador especial. Luego tenemos otra muy útil que es la representación hexadecimal. Otra interesante es la binaria, que emplea el prefijo 0b antes del número en binario. La cuarta y última base es la octal, que usaremos en raras ocasiones y se especifica con el prefijo 0.<br>
**Simbolos**
Como las etiquetas se pueden ubicar tanto en la sección de datos como en la de código, la versatilidad que nos dan las mismas es enorme. En la zona de datos, las etiquetas pueden representar variables, constantes y cadenas. En la zona de código podemos usar etiquetas de salto, funciones y punteros a zona de datos. Las macros y las constantes simbólicas son símbolos cuyo ámbito pertenece al preprocesador, a diferencia de las etiquetas que pertenecen al del ensamblador. Se especifican con las directivas .macro y .equ respectivamente y permiten que el código sea más legible y menos repetitivo.<br>
**Directivas**
Las directivas son expresiones que aparecen en el módulo fuente e indican al compilador que realice determinadas tareas en el proceso de compilación. El uso de directivas es aplicable sólo al entorno del compilador, por tanto varían de un compilador a otro y para diferentes versiones de un mismo compilador. Las directivas más frecuentes en el **as** son:<br>
***-Directivas de asignación:*** Se utilizan para dar valores a las constantes o reservar posiciones de memoria para las variables .byte, .hword, .word, .ascii, .asciz, .zero y .space son directivas que indican al compilador que reserve memoria para las variables del tipo indicado.<br>
***-Directivas de control:*** .text y .data sirven para delimitar las distintas secciones de nuestro módulo. .align alineamiento es para alinear el siguiente dato, rellenando con ceros, de tal forma que comience en una dirección múltiplos del número que especifiquemos en alineamiento, normalmente potencia de 2. Si no especificamos alineamiento por defecto toma el valor de 4.<br>
***-Directivas de operando:*** Se aplican a los datos en tiempo de compilación. En general, incluyen las operaciones lógicas &, |, ∼, aritméticas +, -, *, /, % y de desplazamiento <, >, <<, >>:<br>
***Directivas de Macros:*** Una .macro es un conjunto de sentencias en ensamblador que pueden aparecer varias veces repetidas en un programa con algunas modificaciones.<br>
**1.1.6.** Ensamblar y *linkar* un programa<br>
La traducción o ensamblado de un módulo fuente se realiza con el programa Gnu Assembler, con el siguiente comando:
```as -o nombreprograma.o nombreprograma.s```
El as genera un fichero nombreprograma.o. Para montar (linkar) hay que hacer:
```gcc -o nombreprograma nombreprograma.o```
Una vez hecho ésto, ya tenemos un fichero ejecutable (nombreprograma) que podemos ejecutar o depurar con el gdb.<br>
**1.2.** Enunciados de la práctica<br>
**1.2.2**<br>
**1.2.3**<br>
**1.2.4** Rotaciones y desplazamientos <br>
Los desplazamientos lógicos desplazan los bit del registro fuente introduciendo ceros.El último bit que sale del registro fuente se almacena en el flag C.<br>
Las instrucciones de rotación también desplazan, pero el bit que sale del valor se realimenta. No existe ninguna instrucción para rotar hacia la izquierda ROL, ya que puede simularse con la de rotación a la derecha ROR que sí existe. En estas instrucciones el bit desplazado fuera es el mismo que el que entra, además de dejar una copia en el flag C.<br>
Las instrucciones de rotación con el carry funcionan de manera similar, pero el bit que entra es el que había en el flag C y el que sale va a parar al flag C. Estas instrucciones sólo rotan un bit, al contrario que las anteriores que podían rotar/desplazar varios. La rotación con carry a la derecha es RRX, no existe la contrapartida RLX porque se puede sintetizar con otra instrucción ya existente adcs. Con adcs podemos sumar un registro consigo mismo, que es lo mismo que multiplicar por 2 o desplazar 1 bit hacia la izquierda. Si a esto le añadimos el bit de carry como entrada y actualizamos los flags a la salida, tendremos exactamente el mismo comportamiento que tendría la instrucción RLX.<br>
También podemos forzar el flag C o cualquier otro flag al valor que queramos con la siguiente instrucción.
```msr cpsr_f, # valor```
Donde para calcular el valor hacemos el paso inverso al explicado en gdb. Queremos cambiar los flags a estos valores: N=0, Z=1, C=1 y V=0. Por el orden memorizado de la secuencia NZCV, calculamos el nibble binario, que es 0110. Lo pasamos a hexadecimal 0110 ->6 y lo ponemos en la parte más alta de la constante de 32 bits, dejando el resto a cero<br>
```msr cpsr_f, # 0x60000000```
Todas las instrucciones de rotación en realidad son subinstrucciones que el ensamblador traduce a una instrucción mov. <br>
```LSRs r0, r0, #1```
``` movs r0, r0, LSR #1```
**1.2.5** Instrucciones de multiplicación<br>
Las instrucciones de multiplicación admiten muchas posibilidades, debido a que es una operación en la cual el resultado tiene el doble de bits que cada operando.
|Instrucción| Bits |Nombre| 
|--|--|--|
| mul | 32=32x32 |Multiplicación truncada|
|umull|64=32x32|Multiplicación sin signo de 32bits
|smull|64=32x32|Multiplicación con signo de 32bits
|smulw*|32=32x16|Multiplicación con signo de 32x16bits
|smul**|32=16x16|Multiplicación con signo de 16x16bits
<br>
La instrucción mul realiza una multiplicación truncada, es decir, nos quedamos con los 32 bits inferiores del resultado. Como el signo del resultado es el bit más significativo el cual no obtenemos, esta multiplicación es válida tanto para operandos naturales como para enteros.<br>
<b>2.1</b> Lectura previa <br>
<b> 2.1.1 </b> Modos de direccionamiento del ARM<br>
En la arquitectura ARM los accesos a memoria se hacen mediante instrucciones específicas ldr y str. El resto de instrucciones toman operandos desde registros o valores inmediatos, sin excepciones. En este caso la arquitectura nos fuerza a que trabajemos de un modo determinado: primero cargamos los registros desde memoria, luego procesamos el valor de estos registros con el amplio abanico de instrucciones del ARM, para finalmente volcar los resultados desde registros a memoria. Normalmente se opta por direccionamiento a memoria en instrucciones de procesado en arquitecturas con un número reducido de registros, donde se emplea la memoria como almacén temporal.<br>

**Direccionamiento inmediato.** El operando fuente es una constante, formando parte de la instrucción.
``mov r0, # 1 ``
``add r2, r3, #4``
**Direccionamiento inmediato con desplazamiento o rotación.** Es una variante del anterior en la cual se permiten operaciones intermedias sobre los registros.
``mov r1, r2, LSL #1 /* r1 <- (r2*2) */``
``mov r1, r2, LSL #2 /* r1 <- (r2*4) */``
``mov r1, r3, ASR #3 /* r1 <- (r3/8) */``
Estas instrucciones también se usan implicitamente para la creación de constantes, rotando o desplazando constantes más pequeñas de forma transparente al usuario. Como todas las instrucciones ocupan 32 bits, es técnicamente imposible que podamos cargar en un registro cualquier constante de 32 bits con la instrucción mov. Por esta razón cuando se necesita cargar una constante más compleja en un registro no podemos hacerlo con la instrucción mov, tenemos que recurrir a ldr con direccionamiento a memoria.
Un método para determinar si una constante entra o no en una instrucción mov es pasar la constante a binario y quitar los ceros de la izquierda y de la derecha y contar el número de bits resultante. Si el número de bits es menor o igual que 8, la constante entra en una instrucción mov. <br>
**Direccionamiento a memoria, sin actualizar registro puntero.** Es la forma más sencilla y admite 4 variantes. Después del acceso a memoria ningún registro implicado en el cálculo de la dirección se modifica. Simplemente añade un valor inmediato al registro dado para calcular la dirección. Es muy útil para acceder a elementos fijos de un array, ya que el desplazamiento es constante. Por ejemplo si tenemos r1 apuntando a un array de enteros de 32 bits int a[] y queremos poner a 1 el elemento a[3], lo hacemos así:
``mov r2, # 1 /* r2 <- 1 */``
``str r2, [ r1, #+ 12 ] /* *( r1 + 12) <- r2 */``
<br>
**Direccionamiento a memoria, actualizando registro puntero.** En este modo de direccionamiento, el registro que genera la dirección se actualiza con la propia dirección. De esta forma podemos recorrer un array con un sólo registro sin necesidad de hacer el incremento del puntero en una instrucción aparte.<br>
**2.1.2.** Tipos de datos<br>
**Tipos clasicos de datos.**
|ARM  |Tipo en C  |bits|Rango|
|--|--|--|--|
|.byte  |unsigned char<br>(signed) char|8<br>8|0 a 225<br>-128 a 127
|.hword<br>short|unsigned short int<br>(signed) short int|16<br>16|0 a 65.535<br>-32.768 a 32767|
|.word<br>.int|unsigned int<br>(signed) int<br>unsigned long int<br>(signed) long int|32<br>32<br>32<br>32|0 a 4294967296<br>-2147483648 a 2147483647<br>0 a 4294967296<br>-2147483648 a 2147483647|
|.quad|unsigned long long<br>(signed) long long|64<br>64|0 a 2^64 <br>2^63 a 2 ^63-1
<br>

**Punteros.** Un puntero siempre ocupa 32 bits y contiene una dirección de memoria.<br>
**Vectores.** Todos los elementos de un vector se almacenan en un único bloque de memoria a partir de una dirección determinada. Los diferentes elementos se almacenan en posiciones consecutivas, de manera que el elemento i está entre los i-1 e i+1. Los vectores están definidos siempre a partir de la posición 0. El propio índice indica cuántos elementos hemos de desplazarnos respecto del comienzo del primer elemento. Dado un vector int v[N];, todos los elementos se encuentran en posiciones consecutivas a partir de la dirección de v[0]<br>

**Matrices bidimensionales.** Una matriz bidimensional de N×M elementos se almacena en un único bloque de memoria. Interpretaremos una matriz de N×M como una matriz con N filas de M elementos cada una. Si cada elemento de la matriz ocupa B bytes, la matriz ocupará un bloque de M ×N ×B bytes. Dentro de este bloque, los elementos se almacenan por filas. Primero se guardan todos los elementos de la fila 0, después todos los de la fila 1, etc.<br>

**2.1.3.** Instrucciones de salto<br>
Las instrucciones de salto pueden producir saltos incondicionales (b y bx) o saltos condicionales. En los saltos condicionales añadimos dos o tres letras a la (b/bx), mediante las cuales condicionamos si se salta o no dependiendo del estado de los flags. Estas condiciones se pueden añadir a cualquier otra instrucción, aunque la mayoría de las veces lo que nos interesa es controlar el flujo del programa y así ejecutar o no un grupo de instrucciones dependiendo del resultado de una operación. <br>
La lista completa de condiciones es ésta:<br>
>EQ (equal, igual). Cuando Z está activo (Z vale 1).
>NEQ (not equal, igual). Cuando Z está inactivo (Z vale 0).
>MI (minus, negativo). Cuando N está activo (N vale 1).
>PL (plus, positivo o cero). Cuando N está inactivo (N vale 0).
>CS/HS (carry set/higher or same, carry activo/mayor o igual). Cuando C está activo (C vale 1).
>CC/LO (carry clear/lower, carry inactivo/menor). Cuando C está inactivo (C vale 0).
>VS (overlow set, desbordamiento activo). Cuando V está activo (V vale 1)
>VC (overlow clear, desbordamiento inactivo). Cuando V está inactivo (V vale 0).
>GT (greater than, mayor en complemento a dos). Cuando Z está inactivo y N=V (Z vale 0, N vale V).
>LT (lower than, menor en complemento a dos). Cuando N!=V (N vale not V).
>GE (greater or equal, mayor o igual en complemento a dos). Cuando N=V (N vale V).
>LE (lower or equal, menor o igual en complemento a dos). Cuando Z está activo y N!=V (Z vale 1, N vale not V).
>HI (higher, mayor). Cuando C está activo y Z inactivo (C vale 1, Z vale 0).
>LS (lower or same, menor o igual). Cuando C está inactivo ó Z activo (C vale 0 ó Z vale 1).

**2.1.4.** Estructuras de control de alto nivel
<br>
Las estructuras for y while se pueden ejecutar un mínimo de 0 iteraciones (si la primera vez no se cumple la condición). Para programar en ensamblador estas estructuras se utilizan instrucciones de salto condicional. Previo a la instrucción de salto es necesario evaluar la condición del bucle o de la sentencia if, mediante instrucciones aritméticas o lógicas, con el fin de actualizar los flags de estado.
```bash
int vi , vf , i ;
for ( i= vi ; i <= vf ; i ++ )
{ 
/* Cuerpo del bucle */
 } 
i= vi ;
 while ( i <= vf )
 { 
 /* Cuerpo del bucle */ 
 i ++; }
```
**2.1.5.** Compilación a ensamblador<br>
En el caso de gcc este proceso se hace en dos fases: en una primera se pasa de C a ensamblador, y en una segunda de ensambladador a código compilado. Lo interesante es que podemos interrumpir justo después de la compilación y ver con un editor el aspecto que tiene el código ensamblador generado a partir del código fuente en C. <br>
```bash
# include < stdio .h > 
void main ( void ){
 int i;
 for ( i= 0; i <5; i ++ )
 { printf ( " %d\n " , i );
 } 
 }
```
Después de crear el fichero tipos3.s, lo compilamos con este comando.<br>
``gcc -Os -S -o tipos3a.s tipos3.c``
Con el parámetro -S forzamos la generación del .s en lugar del .o y con -Os le indicamos al compilador que queremos optimizar en tamaño, es decir que queremos código ensamblador lo más pequeño posible, sin importar el rendimiento del mismo.

**2.2.** Enunciados de la práctica<br>
**2.2.1** Suma de elementos de un vector<br>
El vector se denomina vector y tiene 5 elementos de tipo int (entero de 32 bits).
```bash
# include < stdio .h > 
void main ( void ){ 
int i , suma ; 
int vector [5]= {128 , 32 , 100 , -30 , 124}; 
for ( suma = i = 0; i <5; i ++ ){
suma += vector [i ]; 
} 
printf (" La suma es %d \n" , suma ); }
```
```bash
.data
var1 : .asciz " La suma es %d \n"
var2 : .word 128, 32, 100, - 30, 124 

.text
.global main
 
/* Salvamos registros */ 
main : push { r4, lr }
/* Inicializamos variables y apuntamos r2 a var2 */ 
		mov r0, # 5 
		mov r1, # 0 
		ldr r2, = var2 
/* Bucle que hace la suma */ 
bucle : ldr r3, [ r2 ] , # 4 
		add r1, r1, r3 
		subs r0, r0, #1 
		bne bucle 
/* Imprimimos resultado */
		ldr r0, = var1 bl printf
/* Recuperamos registros y salimos */ 
		pop { r4, lr } bx lr
```

