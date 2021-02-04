---
layout: post
title: Bitwise Miscellaneous
permalink: /:collection/cs/bitwise/miscellaneous
---

**Modulo**
- %8 = `n & 0x7`
- %32 = `n & 0x1F`

```
0100_1011 n (75)
0000_0111 0x7
----------
0000_0011 3 (75%8 = 3)
```

**Average without Division**
- `mid = (low + high)/2` - this can go beyond int limit
- `mid = low + (high-low)/2`

```
mid = low + (high-low)>>1
```

**Swap All Odd and Even bits**
`(n & 0x55) << 1 | (n & 0xAA) >> 1`

```
0100_1011 n
1010_1010 0xAA 
----------
0000_1010 (Even bits)
0000_0101 (Even bits)>>1
```
```
0100_1011 n
0101_0101 0x55 
----------
0100_0001 (Odd bits)
1000_0010 (Odd bits)<<1
```
```
1000_0010 (Odd bits)<<1
0000_0101 (Even bits)>>1 |
----------
1000_0111
```

**Reverse Binary Number**
```java
int n = 10;
int reverse = 0;
int lsb = 0;
int s = 32; // size of int
System.out.println(Integer.toString(n, 2));
System.out.println(String.format("%32s", Integer.toBinaryString(n)).replaceAll(" ", "0"));
while (n > 0) {
    reverse <<= 1;
    lsb = n & 1;
    reverse |= lsb;
    n >>= 1;
    s--;
}
reverse <<= s;
System.out.println(String.format("%32s", Integer.toBinaryString(reverse)).replaceAll(" ", "0"));
```

**Count number of Ones**
- bit by bit

```java
while(n>0){
    count += n & 1;
    n >>= 1;
}
```

- 4 bit group map
- 0100 = 1 bit (4)

```java
int[] bits = {0,1,1,2,1,2,2,3,1,2,2,3,2,3,3,4};
while(n>0){
    count += bits[n & 0xF];
    n >>= 4;
}
```

**Create mask for trailing Zero**
`(n & -n) - 1`

```
0100_1000 n
1011_1000 -n &
----------
0000_1000 (n & -n)
----------
0000_0111 (n & -n) - 1
```