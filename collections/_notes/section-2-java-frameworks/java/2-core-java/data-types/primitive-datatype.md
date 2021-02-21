---
layout: post
title: Primitive Datatype
permalink: /:collection/java/primitive-datatype
---


* 8 primitive types represent single values, used for efficiency.
* Wrapper objects degrade performance for basic operations.
* Due to portability requirement, all data types have a strictly defined range.
  * example, int always 32 bits on all platform.
* **Integers** : byte, short, int, long
* **Floating-point** : float, double
* **Characters** : char
* **Boolean** : boolean

Name	| bytes | bits	| Range (From)					| Range (To)                | Deafult   | Note
---		|---    |---	| ---							| ---                       | ---       | ---
byte 	| 1     | 8 	| –128							| 127                       | 0         |
short 	| 2     | 16 	| –32,768						| 32,767                    | 0         |
int 	| 4     | 32 	| –2,147,483,648				| 2,147,483,647             | 0         | 2x10^9                        |
long 	| 8     | 64 	| –9,223,372,036,854,775,808	| 9,223,372,036,854,775,807 | 0         | 9x10^18                       |
float	| 4     | 32	| 1.4e–045						| 3.4e+038                  | 0.0f      | 6-7 significant decimal digits
double	| 8     | 64	| 4.9e–324						| 1.8e+308                  | 0.0d      | 15 significant decimal digits
char	| 2     | 16    | 0                             | 65,536                    | '\u0000'  | unsigned
boolean	|       |       | true or false                 |                           | false     | 

* *byte*, *short*, *int*, and *long*. All of these are signed, positive and negative values. 
* Java, highorder-bit managed by adding **unsigned right shift** (`>>>`) operator, need for unsigned integer eliminated.

|Integers||
---     |---
byte    | for stream of data from a network or file. 
int     | used to control loops and indexes in arrays. For expression evaluation - byte/short promoted to int.
long    | used when large values as result. ex. Speed_of_light, lightyear.
float   | Single precision with less space, used for a fractional component, but not require a large degree of precision.
double  | when need accuracy over many iterative calculations.

* Java uses **16-bit Unicode** for characters, for global portability ranging 0 to 65,536.
	- ASCII are 0 to 127, extended 8-bit character set, ISO-Latin-1, ranges from 0 to 255. 
	- can also be used as an integer type to perform arithmetic operations. example, add two chars or increment value.