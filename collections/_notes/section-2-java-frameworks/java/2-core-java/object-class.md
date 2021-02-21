---
layout: post
title: Object Class
permalink: /:collection/java/object-class
---

* Object - superclass of all classes.
* reference variable of type Object can refer to any object, even to an array.
* getClass(), notify(), notifyAll(), and wait() are declared as final. You may override the others.

# Methods for class : Object

|Object Class Methods||
|---|---|
Object clone( ) 	        |final void notify( ) 
int hashCode( ) 	        |final void notifyAll( ) 
boolean equals(Object obj) 	|final void wait( ), void wait(long milliseconds)
void finalize( ) 	        |final void wait(long milliseconds, int nanoseconds)
String toString( )	        |final Class<?> getClass()
