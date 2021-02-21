---
layout: post
title: JDK vs JRE vs JVM
permalink: /:collection/java/jdk-jre-jvm
---

- **JVM**
  - virtual machine that run the Java bytecodes.
  - **Class loader system** + **runtime data area** + **Execution Engine**
- **JRE**
  - Environment where Java programs runs.
  - [**JVM** + **Java Packages Classes (util, math, lang etc)** + **runtime libraries**]
- **JDK**
  - **JRE** + **Development/debugging tools**
  - (Java compiler javac in its /bin) and tools (ex. javaDoc, debugger)

* For running Java programs on browser/computer you will only install JRE, for development JDK is required.
  * If you are deploying a WebApp with JSP, JDK is required as JSP is converted into Servlets by compilation.

![jdk-jre-jvm]({{site.cdn}}/java/jvm-architecture/jdk-jre-jvm.png)

|Components||
---|---
Compiler|Translate human readable source code in to computer-executable machine code.
Interpreter|Translates the instructions into an intermediate form, which it then executes.
Linker|Combines object modules to form an executable program, done by the linker. Linking function calls.
Loader|Copies programs from a storage device to the main memory, where they can be executed. 
