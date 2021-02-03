---
layout: post
title: Java’s Magic - The ByteCode
permalink: /java/bytecodes
---

![bytecode](https://github.com/arpit04tripathi/files-cdn/raw/cdn/java/core-java/bytecode.png)

- **Bytecode**
  - highly optimized set of instructions executed by JVM.
  - Java compiler creates bytecode rather than executable code.
- **JVM**
  - originally designed as an *interpreter for bytecode*.
  - JVM is implemented for each platform hence portability of bytecode.
- **JIT compiler**
  - selected portions of bytecode are compiled into executable code, on a piece-by-piece demand basis.
  - JIT compiles code as it is needed, during execution. 
  - Entire Java program not compile to executable code all at once, as various run-time checks happen.
  - Not all sequences of bytecode are compiled, only those that will benefit from compilation, remaining code is simply interpreted.