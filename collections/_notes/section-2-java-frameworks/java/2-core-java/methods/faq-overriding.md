---
layout: post
title: Overloading vs Overriding
permalink: /:collection/java/faq-overriding
---

# What is co-variant method overriding?
* original method returns class X, then overridden method **can return sub class** of X.
* this removes casting at client end.
* Example, clone() method originally returns Object, but with co-variant overriding clone return **java.util.Date**.

# Can you prevent overriding a method without using final modifier?
Yes, private constructor. 
* Now, its not possible to extend that class because its constructor will not be accessible in sub class, which is automatically invoked by sub class constructor.
* used in Singleton design pattern, private constructor and static getInstance() to access singleton instance. 
* Use Modifiers – final / static / private

# Questions
* **Can we override a non-static method as static in Java?** - No, compile time error.
* **How do you call super class version of an overriding method in sub class?** - super.parentMethod().
* **Can we override constructor in Java?** - No, constructor are not inherited.
* **Can you overload or override main() method in Java?**
	- **cannot override**, static method.
	- **can overload**, but still JVM will always call `public static void main(String args[])`.
