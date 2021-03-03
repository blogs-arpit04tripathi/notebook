---
layout: post
title: Adapter Pattern
permalink: /:collection/design-patterns/structural/adapter-pattern
---

- TOC
{:toc}

<hr><br>

-	used so that two unrelated interfaces can work together.
-	The object that joins these unrelated interface is called an Adapter.

# Real Life Example 
Mobile charger - Mobile battery needs 3 volts to charge but the normal socket produces either 120V (US) or 240V (India). So the mobile charger works as an adapter between mobile charging socket and the wall socket.

![]({{site.cdn}}/design-patterns/structural-adapter-example.png)

```java
public class Volt {
    private int volts;
    
    public Volt(int v) {this.volts = v;}
    public int getVolts() {return volts;}
    public void setVolts(int volts) {this.volts = volts;}
}
```
```java
public class Socket {
    public Volt getVolt() {return new Volt(120);}
}
```
```java
public interface SocketAdapter {
    public Volt get120Volt();
    public Volt get12Volt();
    public Volt get3Volt();
}
```

# JDK Example - Adapter Design Pattern
- `java.util.Arrays.asList()`
- java.io.InputStreamReader(InputStream) (returns a Reader)
- java.io.OutputStreamWriter(OutputStream) (returns a Writer)

# Two Way Adapter Pattern
- **Class Adapter**
  - This form uses java inheritance and extends the source interface, in our case Socket class.
-	**Object Adapter**
    - This form uses Java Composition and adapter contains the source object.

![]({{site.cdn}}/design-patterns/structural-adapter.png)

```java
//Using inheritance for adapter pattern
public class SocketClassAdapterImpl extends Socket implements SocketAdapter {
    @Override
    public Volt get120Volt() {
        return getVolt();
    }
    @Override
    public Volt get12Volt() {
        Volt v = getVolt();
        return convertVolt(v, 10);
    }
    @Override
    public Volt get3Volt() {
        Volt v = getVolt();
        return convertVolt(v, 40);
    }
    private Volt convertVolt(Volt v, int i) {
        return new Volt(v.getVolts() / i);
    }
}
```
```java
public class SocketObjectAdapterImpl implements SocketAdapter {
    //Using Composition for adapter pattern
    private Socket sock = new Socket();
    @Override
    public Volt get120Volt() {
        return sock.getVolt();
    }
    @Override
    public Volt get12Volt() {
        Volt v = sock.getVolt();
        return convertVolt(v, 10);
    }
    @Override
    public Volt get3Volt() {
        Volt v = sock.getVolt();
        return convertVolt(v, 40);
    }
    private Volt convertVolt(Volt v, int i) {
        return new Volt(v.getVolts() / i);
    }
}
```
```java
public class AdapterPatternTest {
    public static void main(String[] args) {
        testClassAdapter();
        testObjectAdapter();
    }
    private static void testObjectAdapter() {
        SocketAdapter sockAdapter = new SocketObjectAdapterImpl();
        Volt v3 = getVolt(sockAdapter, 3);
        Volt v12 = getVolt(sockAdapter, 12);
        Volt v120 = getVolt(sockAdapter, 120);
        System.out.println("v3 volts using Object Adapter=" + v3.getVolts());
        System.out.println("v12 volts using Object Adapter=" + v12.getVolts());
        System.out.println("v120 volts using Object Adapter=" + v120.getVolts());
    }
    private static void testClassAdapter() {
        SocketAdapter sockAdapter = new SocketClassAdapterImpl();
        Volt v3 = getVolt(sockAdapter, 3);
        Volt v12 = getVolt(sockAdapter, 12);
        Volt v120 = getVolt(sockAdapter, 120);
        System.out.println("v3 volts using Class Adapter=" + v3.getVolts());
        System.out.println("v12 volts using Class Adapter=" + v12.getVolts());
        System.out.println("v120 volts using Class Adapter=" + v120.getVolts());
    }
    private static Volt getVolt(SocketAdapter sockAdapter, int i) {
        switch (i) {
            case 3: return sockAdapter.get3Volt();
            case 12: return sockAdapter.get12Volt();
            case 120: return sockAdapter.get120Volt();
            default: return sockAdapter.get120Volt();
        }
    }
}
```