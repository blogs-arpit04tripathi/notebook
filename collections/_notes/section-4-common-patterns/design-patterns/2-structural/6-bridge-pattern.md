---
layout: post
title: Bridge Pattern
permalink: /:collection/design-patterns/structural/bridge-pattern
---

- TOC
{:toc}

<hr><br>


-	When we have interface hierarchies in both interfaces as well as implementations, then bridge design pattern is used to decouple the interfaces from implementation and hiding the implementation details from the client programs.
-	***Decouple an abstraction from its implementation so that the two can vary independently. The implementation of bridge design pattern follows the notion to prefer Composition over inheritance.***

![]({{site.cdn}}/design-patterns/structural-bridge.png)

- Now we will use bridge design pattern to decouple the interfaces from implementation. UML diagram for the classes and interfaces after applying bridge pattern will look like below image.

> Note - Bridge design pattern can be used when both abstraction and implementation can have different hierarchies independently and we want to hide the implementation from the client application.

```java
public interface Color {
	public void applyColor();
}
```
```java
public abstract class Shape {
 //Composition - implementor
 protected Color color;
 //constructor with implementor as input argument
 public Shape(Color c){
  this.color=c;
 }
 abstract public void applyColor();
}
```
```java
public class RedColor implements Color{
	public void applyColor(){
		System.out.println("red.");
	}
}
```
```java
public class GreenColor implements Color{
	public void applyColor(){
		System.out.println("green.");
	}
}
```
```java
public class Pentagon extends Shape {
	public Pentagon(Color c) {
		super(c);
	}

	@Override
	public void applyColor() {
		System.out.print("Pentagon filled with color ");
		color.applyColor();
	}
}
```
```java
public class Triangle extends Shape{
 public Triangle(Color c) {
  super(c);
 }
 @Override
 public void applyColor() {
  System.out.print("Triangle filled with color ");
  color.applyColor();
 } 
}
```
```java
public class TestBridgePattern {
 public static void main(String[] args) {
  Shape tri = new Triangle(new RedColor());
  tri.applyColor();
  Shape pent = new Pentagon(new GreenColor());
  pent.applyColor();
 }
}
```