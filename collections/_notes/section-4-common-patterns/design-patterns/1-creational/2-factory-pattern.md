---
layout: post
title: Factory Pattern
permalink: /:collection/design-patterns/creational/factory-pattern
---

- TOC
{:toc}

<hr><br>

# Factory Pattern
- Used when we have a ***super class with multiple sub-classes*** and ***based on input***, we need to ***return one of the sub-class***.
- Responsibility of instantiation shifted from client program to factory class.
- Superclass can be interface, abstract class or a normal class.
- Factory class can be singleton or have a method(return subclass) as static.
- Based on input, subclass object is created.

```java
public abstract class Computer {	
  public abstract String getRAM();
  public abstract String getHDD();
  public abstract String getCPU();

  @Override
  public String toString(){
    return String.format("RAM= %s , HDD= %s, CPU= %s" , this.getRAM(), this.getHDD(), this.getCPU());
  }
}
```
```java
public class PC extends Computer {
  private String ram;
  private String hdd;
  private String cpu;

  public PC(String ram, String hdd, String cpu){
    this.ram=ram;    this.hdd=hdd;    this.cpu=cpu;
  }
  @Override
  public String getRAM() {return this.ram;}
  @Override
  public String getHDD() {return this.hdd;}
  @Override
  public String getCPU() {return this.cpu;}
}
```
```java
public class Server extends Computer {
  private String ram;
  private String hdd;
  private String cpu;

  public Server(String ram, String hdd, String cpu){
    this.ram=ram;    this.hdd=hdd;    this.cpu=cpu;
  }
  @Override
  public String getRAM() {return this.ram;}
  @Override
  public String getHDD() {return this.hdd;}
  @Override
  public String getCPU() { return this.cpu; }
}
```
```java
public class ComputerFactory {
    public static Computer getComputer(String type, String ram, String hdd, String cpu) {
        if ("PC".equalsIgnoreCase(type))
            return new PC(ram, hdd, cpu);
        else if ("Server".equalsIgnoreCase(type))
            return new Server(ram, hdd, cpu);
        return null;
    }
}
```
```java
public class TestFactory {
    public static void main(String[] args) {
        Computer pc = ComputerFactory.getComputer("pc", "2 GB", "500 GB", "2.4 GHz");
        Computer server = ComputerFactory.getComputer("server", "16 GB", "1 TB", "2.9 GHz");
        System.out.println("Factory PC Config::" + pc);
        System.out.println("Factory Server Config::" + server);
    }
}
// Output
Factory PC Config::RAM= 2 GB, HDD=500 GB, CPU=2.4 GHz
Factory Server Config::RAM= 16 GB, HDD=1 TB, CPU=2.9 GHz
```

# Advantages-Factory Design Pattern
- code for interface rather than implementation.
- instantiation responsibility moved out of client code.
- we can easily change PC implementation without affecting client code.
- abstraction between implementation and client classes through inheritance.

# JDK Examples-Factory Design Pattern
- **getInstance()** methods in java.util.Calendar, ResourceBundle and NumberFormat uses Factory pattern.
- **valueOf()** method in wrapper classes like Boolean, Integer etc.