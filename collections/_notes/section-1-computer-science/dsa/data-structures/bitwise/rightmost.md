---
layout: post
title: Rightmost Bit Operations
permalink: /:collection/cs/bitwise/rightmost
---


**Toggle rightmost One bit**
`n & n-1`

```
0100_0110 n
0100_0101 n-1 &
----------
0100_0100
```

```
0100_0100 n
0100_0011 n-1 &
----------
0100_0000
```

**Isolate rightmost One bit**
`n & -n`

```
0100_1010 n
1011_0110 -n & (2's complement)
----------
0000_0010
```

**Isolate rightmost Zero bit**
`~n & n+1`

```
0100_1011 n
1011_0100 ~n
0100_1100 n+1 &
----------
0000_0100
```
