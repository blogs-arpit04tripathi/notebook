---
layout: post
title: PATH vs CLASSPATH
permalink: /:collection/java/path-vs-classpath
---

- **NoClassDefFoundError** and **ClassNotFoundException** both occur when class is not found at runtime.
- Due to incorrect/misconfigured CLASSPATH.

**PATH**
* JDK_HOME/bin added to PATH env variable. 
* can’t be overridden by any Java settings. 
* OS finds binary and command typed in shell. Example - java, javac.
* Windows - set PATH=%PATH%; C:\Program Files\Java\JDK1.6.20\bin
* UNIX/Linux - export PATH = ${PATH}:/opt/Java/JDK1.6.18/bin

**CLASSPATH**
* Used by classloader to find bytecodes stored as .class. 
* Inicludes all directories with .class and JAR file required by your Java application. 
* can be overridden by command line: -classpath or -cp to both "java" and "javac" or by using ClassPath attribute in Manifest file inside JAR archive.
* Windows         - set CLASSPATH = %CLASSPATH%;C:\ProgramFiles\Java\JDK1.6.20\lib
* UNIX/Linux     - export CLASSPATH=${CLASSPATH}:/opt/Java/JDK1.6.18/lib

# ClassNotFoundException
- Occurs when you try to load a class at runtime using Class.forName() or loadClass() methods and requested classes are not found in classpath.
- This is a checked Exception derived from java.lang.Exception class and you need to provide explicit handling for it.
- Common Scenario - We try to run application without updating classpath with JAR files.
- This exception also occurs when you have two class loaders and if a ClassLoader tries to access a class which is loaded by another classloader in Java.
- **Java ClassLoader** is a part of Java Runtime Environment that dynamically loads Java classes in JVM(Java Virtual Machine). The Java Runtime System does not need to know about files and files system because of classloaders.

# NoClassDefFoundError
- Occurs when class was present during compile time and program was compiled and linked successfully but class was not present during runtime.
- It is error which is derived from **LinkageError**.
  - Linkage error occurs when a class has some dependencies on another class and latter class changes after compilation of former class. NoClassFoundError is the result of implicit loading of class because of calling a method or accessing a variable from that class.
- This error is more difficult to debug and find the reason why this error occurred. So in this case you should always check the classes which are dependent on this class.

# ClassNotFoundException Vs NoClassDefFoundError
- ClassNotFoundException is an exception while NoClassDefFoundError is an error.
- ClassNotFoundException occurs when classpath is does not get updated with required JAR files while error occurs when required class definition is not present at runtime.