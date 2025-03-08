---
title: 'Arithmetic Logic Unit (ALU)'
description: 'Here is a sample of some basic Markdown syntax that can be used when writing Markdown content in Astro.'
pubDate: 'Jun 19 2024'
heroImage: '/Electronic-Blog/alu/ALU_portada2.webp'
---
#### Proyecto
Realizar el diseño y la implementación mediante compuertas lógicas básicas (circuitos integrados), una ALU de dos
entradas (cada una de 4 bits), la cual debe realizar las siguientes operaciones:

- Aritmeticas:
	- Suma
	- Resta (cuando A > B)
	- Multiplicador binario (multiplicando con B2B1B0 y el multiplicador con A1A0).
	- Comparador de magnitud (visualización mediante 3 leds)
- Lógicas:
	- OR
	- AND
	- XOR
	- NOT A

#### Solución
Para las operaciones aritméticas, comenzamos con la suma, ya que, al ser una operación más básica, puede servir como fundamento para la resta.

Para diseñar un sumador de 4 bits, es fundamental analizar la tabla de verdad de un sumador de 2 bits, ya que esta nos permite extender el concepto y sumar la cantidad de bits que necesitemos.

![tabla de verdad sumador](/Electronic-Blog/alu/imagen1alu.webp)

Visto con compuertas logicas:

![circuito sumador completo](/Electronic-Blog/alu/imagen2alu.webp)

Siguiendo esta misma lógica, podemos adaptar el sumador a nuestro caso y así obtener el diseño de un sumador de 4 bits

![sumador 4 bits](/Electronic-Blog/alu/imagen3alu1.webp)


Una vez diseñado el sumador de 4 bits, podemos avanzar hacia la implementación de un restador de 4 bits. Para ello, se añade un circuito de selección y un circuito de adaptación que permite realizar la resta mediante compuertas XOR y AND obteniendo lo siguente 

![sumador/restador](/Electronic-Blog/alu/imagen4alu1.webp)

Para implementar la funcionalidad de sumador/restador, se
utilizó un sumador integrado de 4 bits (74LS283), junto con 4
compuertas XOR (74LS86), 1 compuerta NOT (74LS04) y
una compuerta AND (74LS08). Esta elección se hizo con el
objetivo de optimizar el presupuesto, evitando tener que
implementar completamente un circuito separado para el
restador.

![simu sumador/restador](/Electronic-Blog/alu/imagen8alu.webp)

Este enfoque se apoya en el concepto del complemento a 1.
Esta técnica consiste en obtener el complemento de un número
binario al cambiar todos los 1s por 0s y todos los 0s por 1s.
Aunque en algunas Unidades Lógico-Aritméticas (ALU) se
utiliza el complemento a 2 para representar números
negativos, en esta práctica no fue necesario recurrir a esta
técnica.

Para el diseño del multiplicador se usa un sumador y 6 compuertas AND, en nuestro caso para simplificar el circuito se usó un integrado 74LS283

![Multiplicador](/Electronic-Blog/alu/imagen5alu.webp)

En el comparadaor de magnitud se diseño un circuito con compuertas AND OR NOT NOR 

![Comparador](/Electronic-Blog/alu/imagen6alu.webp)

Para la parte lógica del circuito, se utilizan los integrados 7408 (AND), 7432 (OR), 7486 (XOR) y 7404 (NOT). Además, se emplean multiplexores para la selección de operaciones, los cuales están conectados a un switch que permite intercambiar entre las distintas funciones a visualizar.

![Operaciones lógicas](/Electronic-Blog/alu/imagen7alu.webp)

**Nota: Las simulaciones en CircuitVerse y Proteus pueden visualizarse en el enlace que dejaré al final del post, permitiendo evidenciar claramente su funcionamiento.**

La parte más compleja del circuito, en mi opinión, fue la decodificación o conversión de 5 bits binarios a BCD, ya que la salida debía visualizarse a través de displays de 7 segmentos. Para lograr esta conversión, basándonos en el algoritmo de corrimiento XC3, utilizamos dos sumadores integrados (74LS283), dos comparadores (7485) y dos conversores BCD a 7 segmentos (74LS48).

Aprendí este proceso gracias al blog <a href="https://wilaebaelectronica.blogspot.com/2017/01/decodificador-binario-a-bcd-de-5-bits.html" target="_blank" rel="noopener noreferrer">Wilaeba electronica</a>, por lo que no lo incluí en las simulaciones. Sin embargo, quienes deseen recrearlo o comprenderlo en mayor detalle pueden visitar el sitio web o integrarlo en la simulación proporcionada.

![Decodificacion](/Electronic-Blog/alu/decodificacion.webp)

Cada salida de operación se conecta a un multiplexor para seleccionar la función deseada. En la implementación del circuito, se estableció que la selección binaria 'A-' representa la suma/resta, mientras que 'B' corresponde a la multiplicación.


#### Montaje

Acá muestro el montaje que me tocó realizar cuando me asignaron este laboratorio tanto la parte logica como aritmética están unidas pero para mayor entendimiento ya que el circuito es gigante separé las imagenes.

- Aritmeticas:
	- ![Operaciones aritméticas](/Electronic-Blog/alu/imagenalupartearitmética.webp)
- Lógicas:
	- ![Operaciones logicas](/Electronic-Blog/alu/imagenalupartelogica.webp)


**Descarga la simulación de proteus aquí:** 
<a href="/Electronic-Blog/ALU.pdsprj" download="ALU.pdsprj">  Descargar ALU_proteus</a>

**Acede a la simulación de circuitverse aquí:**
<a href="https://circuitverse.org/simulator/embed/untitled-0ac6726a-a196-4eea-9282-3a3e7dec3905" target="_blank" rel="noopener noreferrer">  Circuitverse_sum/res/comparador</a>