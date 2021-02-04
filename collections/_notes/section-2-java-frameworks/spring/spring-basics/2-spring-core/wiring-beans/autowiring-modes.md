---
layout: post
title: Autowiring Modes
permalink: /:collection/spring/autowiring-modes
---

**Autowiring**
-	Autowiring enables you to inject the object dependency implicitly. 
-	It internally uses setter or constructor injection.
-	Autowiring can't be used to inject primitive and string values. It works with reference only.
- **Advantage** - requires less code as need not to write code to inject the dependency explicitly.
- **Disadvantage** - No control of programmer. It can't be used for primitive and string values.
- **@Autowired** - First checks byType. If conflict, uses byName.

| Autowiring Modes ||
|---|---|
|no|	It is the default autowiring mode. It means no autowiring by default.|
|byName|	injects the object dependency according to name of the bean. <br>Property/bean name must be same. It internally calls setter method.|
|byType|	injects the object dependency according to type. <br>So, property name and bean name can be different, but only 1 bean of that type should be there.<br>It internally calls setter method.|
|constructor|	injects the dependency by calling the constructor of the class. <br>It calls the constructor having largest number of parameters. (0,1,2 args constructor --> 2args called)|

# byName autowire mode
```java
public class B {  
 B(){System.out.println("b is created");}  
 void print(){System.out.println("hello b");}  
} 
```
```xml
<bean id="b" class="org.sssit.B"></bean>  
<bean id="a" class="org.sssit.A" autowire="byName">
```
```java
public class A {  
 B b;  
 A(){System.out.println("a is created");}  
 // getter setter
 void print(){System.out.println("hello a");}
 void display(){ print();  b.print();}  
}
```

# byType autowiring mode
```xml
<bean id="b1" class="org.sssit.B"></bean>  
<bean id="a" class="org.sssit.A" autowire="byType"></bean> 
```
If multiple bean of one type, it will not work and throw exception. Let's see the code where are many bean of type B.
```xml
<bean id="b1" class="org.sssit.B"></bean>  
<bean id="b2" class="org.sssit.B"></bean>  
<bean id="a" class="org.sssit.A" autowire="byName"></bean>  
```

# constructor autowiring mode
```xml
<bean id="b" class="org.sssit.B"></bean>  
<bean id="a" class="org.sssit.A" autowire="constructor"></bean> 
```

# no autowiring mode
```xml
<bean id="b" class="org.sssit.B"></bean>  
<bean id="a" class="org.sssit.A" autowire="no"></bean> 
```

* ApplicationEvent
* ApplicationEventPublisher
* ApplicationEventPublisherAware