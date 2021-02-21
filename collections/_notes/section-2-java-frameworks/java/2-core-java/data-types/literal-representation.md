---
layout: post
title: Literal Representation
permalink: /:collection/java/literal-representation
---


|Representation||
---         |---
Octal       | leading zero, normal decimal numbers cannot have a leading zero.
Hexadecimal | leading zero-x, (0x or 0X).
Long        | 0x7ffffffffffffffL or 9223372036854775807L is the largest long.
Binary      | prefix the value with 0b or 0B.

```java
int x = 123_456_789;            // the value given to x will be 123,456,789.
int x = 0b1101_0101_0001_1010;  // underscores discarded on compile
```

### Floating-Point Literals
* suffix that specifies a power of 10 - 6.022E23, 314159E–05, and 2e+100.
* A floating-point literal is of type float if it ends with the letter F or f.
* otherwise its type is double and it can optionally end with the letter D or d .
* Hexadecimal floating-point literals - 0x12.2P2(=72.5).
  * P is called **binary exponent**, power-of-two to be multiplied.

![octal-decimal-computation]({{site.cdn}}/java/core-java/octal-decimal-computation.png)

### Character Literals
* directly as 'a', 'z', and '@'. 
* octal notation, ' \141' is the letter 'a'. 
* hexadecimal, '\u0061' is 'a'.

Escape Sequence	| Description
---|---
\r 		| Carriage return
\n 		| New line (line feed)
\f 		| Form feed
\t 		| Tab
\b 		| Backspace
\ddd 	| Octal character (ddd)
\uxxxx 	| Hexadecimal Unicode (xxxx)
\' 		| Single quote
\" 		| Double quote
\\ 		| Backslash
