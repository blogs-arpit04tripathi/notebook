---
layout: post
title: Builder Pattern
permalink: /:collection/design-patterns/creational/builder-pattern
---

- TOC
{:toc}

<hr><br>

# Builder Pattern

- Issues with Factory and Abstract Factory when the Object contain a lot of attributes.
  -	Too Many arguments to be passed
  -	optional parameters need to send as NULL.
- Probable Solution (But Not)
  -	provide a constructor with required parameters and then setter methods for optional parameters. 
  -	Problem - Inconsistent Object state until all attributes are set explicitly.
- Builder pattern solves the issue with
  - large number of optional parameters 
  -	inconsistent state
- ***It provides a way to build the object step-by-step and return the final constructed Object***.
- Builder Design Pattern
  -	 static nested class 
  -	 copy all the arguments from the outer class to the Builder class.
  -	 Builder class - public constructor for required attributes.
  -	 Builder class – setters for optional attributes, returns same Builder object after setting the optional attribute.
  -	Provide build() that will return the final Object needed by client program.

![]({{site.cdn}}/design-patterns/creational-builder.png)

```java
// Computer - only getter & no public constructor, get Computer object only via ComputerBuilder.
public class Computer {
    //required parameters
    private String HDD;
    private String RAM;
    //optional parameters
    private boolean isGraphicsCardEnabled;
    private boolean isBluetoothEnabled;

    // getter for all 4 fields

    private Computer(ComputerBuilder builder) {
        this.HDD = builder.HDD;
        this.RAM = builder.RAM;
        this.isGraphicsCardEnabled = builder.isGraphicsCardEnabled;
        this.isBluetoothEnabled = builder.isBluetoothEnabled;
    }

    //Builder Class
    public static class ComputerBuilder {
        //required parameters
        private String HDD;
        private String RAM;
        // optional parameters
        private boolean isGraphicsCardEnabled;
        private boolean isBluetoothEnabled;

        public ComputerBuilder(String hdd, String ram) {
            this.HDD = hdd;
            this.RAM = ram;
        }
        public ComputerBuilder setGraphicsCardEnabled(boolean isGraphicsCardEnabled) {
            this.isGraphicsCardEnabled = isGraphicsCardEnabled;
            return this;
        }
        public ComputerBuilder setBluetoothEnabled(boolean isBluetoothEnabled) {
            this.isBluetoothEnabled = isBluetoothEnabled;
            return this;
        }
        public Computer build() {
            return new Computer(this);
        }
    }
}
```
```java
public class TestBuilderPattern {
    public static void main(String[] args) {
        //Using builder to get object without any inconsistent state or arguments management issues
        Computer comp = new Computer.ComputerBuilder("500 GB", "2 GB").setBluetoothEnabled(true).setGraphicsCardEnabled(true).build();
    }
}
```

# JDK Example-Builder Design Pattern
-	java.lang.StringBuilder#append() (unsynchronized)
-	java.lang.StringBuffer#append() (synchronized)