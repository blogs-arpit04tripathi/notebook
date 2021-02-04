---
layout: post
title: kth Bit Operations
permalink: /:collection/cs/bitwise/kth-bit
---


**Check Kth Bit (Least Significant) is set?**
`(n & 1<<k-1) > 0`

```
k = 4
0000_1000 1<<k-1
```
```
0100_1011 n
0000_1000 1<<k-1  &
----------
0000_1000
```

**Set Kth Bit (Least Significant) is set?**
`(n | 1<<k-1) > 0`

```
k = 4
0000_1000 1<<k-1
```
```
0100_0011 n
0000_1000 1<<k-1  |
----------
0100_1011
```

**Clear Kth Bit (Least Significant) is set?**
`(n & ~(1<<k-1)) > 0`

```
k = 4
0000_1000 1<<k-1
1111_0111 1<<k-1 ~
```
```
0100_1011 n
1111_0111 ~(1<<k-1)  &
----------
0100_0011
```

**Toggle Kth Bit (Least Significant) is set?**
`(n ^ 1<<k-1) > 0`

```
k = 4
0000_1000 1<<k-1
```
```
0100_0011 n
0000_1000 1<<k-1  ^
----------
0100_1011
```
