---
layout: post
title: Power of 2
permalink: /:collection/cs/ds/bitwise/power-2
---


**Is power of 2**
`n & n-1 == 0`

```
0100_1011 n
0100_1010 n-1 &
----------
0100_1010  (not 0, not power of 2)
```

```
0100_0000 n
0011_1111 n-1 &
----------
0000_0000  (0, power of 2)
```

**Multiply power of 2**
`(n x 2^k) == n <<k`
```
0001_1011 n
----------
1101_1000  n << 3
```

**Divide by power of 2**
`(n / 2^k) == n >>k`
```
0001_1011 n = 27 (divide by 8)
----------
0000_0011  n >>3
```
