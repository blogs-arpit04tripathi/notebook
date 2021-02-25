---
layout: post
title: Get Annotations using Reflection
permalink: /:collection/java/annotations/annotations-reflection
---

* Annotations with **RUNTIME** retention policy can be queried at run time using *reflection*.
* Reflection - feature to get info about a class at run time. (java.lang.reflect package)
* Class object – obtain by .getClass( ) of Object.

```java
final Class<?> getClass( )
```
* getMethod( ), getField( ), and getConstructor( ) return objects of type Method, Field, and Constructor.

```java
Method getMethod(String methName, Class<?> ... paramTypes)    // NoSuchMethodException can be thrown
```
* Class, Method, Field, or Constructor object - getAnnotation( ) obtains a specific annotation associated with that object.

```java
<A extends Annotation> getAnnotation(Class<A> annoType)    // null if not found
```
```java
import java.lang.annotation.*;
import java.lang.reflect.*;
@Retention(RetentionPolicy.RUNTIME)
@interface MyAnno {
    String str();
    int val();
}
class Meta {
    @MyAnno(str = "Annotation Example", val = 100) // Annotate a method.
    public static void myMeth() {
        Meta ob = new Meta();
        try {
            Class < ? > c = ob.getClass();
            Method m = c.getMethod("myMeth");
            // Method m = c.getMethod("myMeth", String.class, int.class);
            // myMeth(String str, int i){}
            MyAnno anno = m.getAnnotation(MyAnno.class); // get single annotation
            System.out.println(anno.str() + " " + anno.val());
            Annotation annos[] = ob.getClass().getAnnotations(); // get all annotations
            System.out.println("All annotations for myMeth:");
            for (Annotation a: annos) {
                System.out.println(a);
            }
        } catch (NoSuchMethodException exc) {
            System.out.println("Method Not Found.");
        }
    }
    public static void main(String args[]) {
        myMeth();
    }
}
// Output
All annotations for myMeth:
@What(description = An annotation test method)
@MyAnno(str = Testing, val = 100)
```
