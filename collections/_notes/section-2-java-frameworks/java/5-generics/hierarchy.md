---
layout: post
title: Generic Class Hierarchies
permalink: /:collection/java/generics/hierarchy
---

- TOC
{:toc}

<hr><br>

# Generic Superclass
```java
class Gen<T> {
  T ob;    
  Gen(T o) { ob = o; }
  T getob() { return ob; }
}
```
```java
class Gen2<T> extends Gen<T> {      // defines type T
   Gen2(T o) { super(o); }
}
```
```java
class Gen2<T, V> extends Gen<T> {   // defines type T and V both.
  V ob2;
  Gen2(T o, V o2) {
      super(o);                     // Type arguments needed by generic superclass
      ob2 = o2;
  }
  V getob2() { return ob2; }
}
```

* **Gen2** does not use the type parameter **T** except to support the **Gen** superclass.
* **A generic class can act as a superclass or be a subclass.**
* **Type arguments needed by a generic superclass must be passed up the hierarchy by all subclasses.**
* **Constructor arguments must be passed up a hierarchy.**

# Generic Subclass 
* Non-generic class can have generic subclass.

```java
class NonGen {
  int num;
  NonGen(int i) { num = i; }
  int getnum() { return num; }
}

class Gen<T> extends NonGen {
  T ob;                 // declare an object of type T
  Gen(T o, int i) {
	super(i);           // super constructor as 1st statement
	ob = o;
  }
  T getob() { return ob; }
}

// main() method
Gen<String> w = new Gen<String>("Hello", 47);
System.out.print(w.getob() + " ");
System.out.println(w.getnum());
```

# Run-Time Type Comparisons Within a Generic Hierarchy

**instanceof** - returns true if an object is of the specified type or can be cast to the specified type.

```java
class Gen<T> {
  T ob;
  Gen(T o) { ob = o; }
  T getob() { return ob; }
}

class Gen2<T> extends Gen<T> {
  Gen2(T o){super(o);}
}

class HierDemo3 {
public static void main(String args[]) {.
 Gen<Integer> iOb = new Gen<Integer>(88);
 Gen2<Integer> iOb2 = new Gen2<Integer>(99);
 Gen2<String> strOb2 = new Gen2<String>("Generics Test");

 if(iOb2 instanceof Gen2<?>)   {sysout("iOb2 is instance of Gen2");}        // true
 if(iOb2 instanceof Gen<?>)    {sysout ("iOb2 is instance of Gen");}        // true
 if(strOb2 instanceof Gen2<?>) {sysout ("strOb2 is instance of Gen2");}     // true
 if(strOb2 instanceof Gen<?>)  {sysout ("strOb2 is instance of Gen");}      // true
 if(iOb instanceof Gen2<?>)    {sysout ("iOb is instance of Gen2");}        // false
 if(iOb instanceof Gen<?>)     {sysout ("iOb is instance of Gen");}         // true
 // if(iOb2 instanceof Gen2<Integer>)   sysout ("iOb2 is instance of Gen2<Integer>");
 // can't be compiled, generic type info does not exist at run time.
}
```
* wildcard enables instanceof to determine if iOb2 is an object of any type of Gen2.

# Casting
* can cast one instance of a generic class into another only if the two are compatible and their type arguments are the same.

```java
(Gen<Integer>) iOb2     // legal - because iOb2 includes an instance of Gen<Integer>.
(Gen<Long>) iOb2        // illegal - is not legal because iOb2 is not an instance of Gen<Long>.
```

# Overriding Methods in a Generic Class
```java
class Gen<T> {
    T ob;
    Gen(T o) { ob = o; }
    T getob() {
        sysout("Gen's getob():");
        return ob;
    }
}

class Gen2<T> extends Gen<T> {
    Gen2(T o) { super(o); }
    T getob() {
        sysout("Gen2's getob(): ");
        return ob;
    }
}
```

# Type Inference with Generics
* **<>, diamond operator**, to tell the compiler to infer the type arguments needed by the constructor in the new expression.

```java
MyClass<Integer,String> mcOb = new MyClass<Integer,String>(98, "A String");
MyClass<Integer,String> mcOb = new MyClass<>(98, "A String");
boolean isSame(MyClass<T,V> o) {
    return (ob1 == o.ob1 && ob2 == o.ob2) ? true : false;
}
if (mcOb.isSame(new MyClass<>(1, "test")))
    System.out.println("Same");
```
