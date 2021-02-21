---
layout: post
title: Cloning
permalink: /:collection/java/marker-interface/cloning
---

- TOC
{:toc}

<hr><br>

# Difference between shallow cloning and deep cloning of objects?
- The **default** behavior of an object’s clone() method automatically yields a **shallow copy**.
- So to achieve a deep copy the classes must be edited or adjusted.

# Shallow copy
- Generally clone method of an object, creates a new instance of the same class and copies all the fields to the new instance and returns it. This is called **shallow copy**.
- Object class provides a clone() method and provides support for the shallow copy. It returns ‘Object’ as type and you need to explicitly cast back to your original object.
- Since the Object class has the clone method, you cannot use it in all your classes. The class which you want to be cloned should implement clone method and overwrite it. It should provide its own meaning for copy or to the least it should invoke the super.clone(). 
- Also you have to implement Cloneable marker interface or else you will get **CloneNotSupportedException**. When you invoke the `super.clone()` then you are dependent on the Object class’s implementation and what you get is a shallow copy.

# Deep copy
- When you need a deep copy then you need to implement it yourself.
- When the copied object contains some other object its references are copied recursively in deep copy.
- When you implement deep copy be careful as you might fall for cyclic dependencies.
- If you don’t want to implement deep copy yourselves then you can go for serialization. It does implements deep copy implicitly and gracefully handling cyclic dependencies.

ToDo
* [Copy Constructor versus Cloning](https://programmingmitra.blogspot.in/2016/05/java-cloning-copy-constructor-versus-Object-clone-or-cloning){:target="_blank"}
* [Even Copy Constructors Are Not Sufficient](https://www.programmingmitra.com/2017/01/java-cloning-why-copy-constructors-are-not-sufficient-or-good.html){:target="_blank"}
* Shallow vs Deep Copy
* [Java-cloning-copy-constructor-versus-Object-clone-or-cloning](https://programmingmitra.blogspot.in/2017/01/Java-cloning-copy-constructor-versus-Object-clone-or-cloning.html){:target="_blank"}
* [java-cloning-why-copy-constructors-are-not-sufficient-or-good](https://programmingmitra.blogspot.in/2017/01/java-cloning-why-copy-constructors-are-not-sufficient-or-good.html){:target="_blank"}
* [Java-Cloning-Types-of-Cloning-Shallow-Deep-in-Details-with-Example](https://programmingmitra.blogspot.in/2016/11/Java-Cloning-Types-of-Cloning-Shallow-Deep-in-Details-with-Example.html){:target="_blank"}
* [shallow-and-deep-java-cloning](https://dzone.com/articles/shallow-and-deep-java-cloning){:target="_blank"}
