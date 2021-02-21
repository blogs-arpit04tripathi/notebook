---
layout: post
title: Generics in Java
permalink: /:collection/java/generics
---

- TOC
{:toc}

<hr><br>

# What are Generics?

* ***parameterized types***. (generic class or generic method)
* creating classes, interfaces, and methods that will work in a type-safe manner with various kinds of data. 
* **all type-casts are automatic and implicit.**
* Many algorithms are same irrespective of data type, stack is same for **Integer, String, Object**, or **Thread**. 
* **collection classes can now be used with complete type safety.**
* Java compiler creates only one **Gen** and substitutes necessary casts, to behave as specific version of **Gen** were created. 
* process of removing generic type information is called **erasure**.

```java
class Gen<T> {
    T ob;
    Gen(T o) {ob = o;}
    T getob() {return ob;}
    void showType() {
        sysout(ob.getClass().getName());
    }
}
Gen<Integer> iOb = new Gen<Integer>(88);
iOb = new Gen<Double>(88.0); // Error!
```

# Generics Work Only with Reference Types
* cannot use a primitive type, **int** or **char**. 
* **iOb** and **strOb** of type **Gen\<T>**, but not type compatible with each other.

# How Generics Improve Type Safety – What if we use Object
* First, **explicit casts** must be employed to retrieve the stored data. 
* Second, many kinds of type **mismatch errors cannot be found until run time**.

```java
int v = (Integer) iOb.getob();
iOb = strOb; // compiles, conceptually wrong!
v = (Integer) iOb.getob(); // run-time error!
```
```java
class_name<type_arg_list>
var_name = new class_name<type_arg_list>(constructor_arg_list);
```
```java
class TwoGen<T,V>{
    T ob1;
    V ob2;
    TwoGen(T o1, V o2) {
        ob1 = o1;
        ob2 = o2;
    }
}
TwoGen<Integer,String> tgObj = new TwoGen<Integer,String>(88, "Generics");
TwoGen<String,String> x = new TwoGen<String,String>("A", "B");
```
