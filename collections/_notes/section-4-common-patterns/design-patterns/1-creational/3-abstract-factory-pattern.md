---
layout: post
title: Abstract Factory Pattern
permalink: /:collection/design-patterns/creational/abstract-factory-pattern
---

- TOC
{:toc}

<hr><br>

# Abstract Factory Pattern
-	Abstract Factory pattern is ***factory of factories***.
-	In factory design patter, we have a single Factory class that returns the different sub-classes based on the input provided and factory class uses if-else or switch statement to achieve this.
-	In Abstract Factory pattern, we get rid of if-else block and have a factory class for each sub-class and then an Abstract Factory class that will return the sub-class based on the input factory class.

```java
public interface ComputerAbstractFactory {
  public Computer createComputer();
}
```
```java
public class ComputerFactory {
    public static Computer getComputer(ComputerAbstractFactory factory) {
        return factory.createComputer();
    }
}
```
```java
public class PCFactory implements ComputerAbstractFactory {
    private String ram;
    private String hdd;
    private String cpu;
    public PCFactory(String ram, String hdd, String cpu) {
        this.ram = ram;
        this.hdd = hdd;
        this.cpu = cpu;
    }
    @Override
    public Computer createComputer() {
        return new PC(ram, hdd, cpu);
    }
}
```
```java
public class ServerFactory implements ComputerAbstractFactory {
    private String ram;
    private String hdd;
    private String cpu;
    public ServerFactory(String ram, String hdd, String cpu) {
        this.ram = ram;
        this.hdd = hdd;
        this.cpu = cpu;
    }
    @Override
    public Computer createComputer() {
        return new Server(ram, hdd, cpu);
    }
}
```
```java
public class TestAbstractFactoryPattern {
    public static void main(String[] args) {
        testAbstractFactory();
    }
    private static void testAbstractFactory() {
        Computer pc = ComputerFactory.getComputer(new PCFactory("2 GB", "500 GB", "2.4 GHz"));
        Computer server = ComputerFactory.getComputer(new ServerFactory("16 GB", "1 TB", "2.9 GHz"));
        System.out.println("AbstractFactory PC Config::" + pc);
        System.out.println("AbstractFactory Server Config::" + server);
    }
}
```

# Advantages of Abstract Factory Design Pattern
-	code for interface rather than implementation.
-	factory of factories, ***easily extended for more products***.
-	can add subclass Laptop and LaptopFactory.
-	Robust and ***avoid conditional logic*** of Factory pattern.

# JDK Examples-Abstract Factory Design Pattern
-	javax.xml.parsers.DocumentBuilderFactory#newInstance()
-	javax.xml.transform.TransformerFactory#newInstance()
-	javax.xml.xpath.XPathFactory#newInstance()

![]({{site.cdn}}/design-patterns/creational-AbstractFactoryPattern.png)