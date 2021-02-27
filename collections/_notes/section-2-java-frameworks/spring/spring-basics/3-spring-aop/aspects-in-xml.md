---
layout: post
title: Declaring aspects in XML
permalink: /:collection/spring/aop/aspects-in-xml
---


If need to declare aspects without annotating the advice class, then use XML configuration, ie. For 3rd party libraries.

|AOP configuration element|	Purpose|
|---|---|
|\<aop:advisor>|	Defines an AOP advisor.|
|\<aop:after>|	Defines an AOP after advice (regardless of whether the advised method returns successfully).|
|\<aop:after-returning>|	Defines an AOP after-returning advice.|
|\<aop:after-throwing>|	Defines an AOP after-throwing advice.|
|\<aop:around>|	Defines an AOP around advice.|
|\<aop:aspect>|	Defines an aspect.|
|\<aop:aspectj-autoproxy>|	Enables annotation-driven aspects using @AspectJ.|
|\<aop:before>|	Defines an AOP before advice.|
|\<aop:config>|	The top-level AOP element. Most \<aop:*> elements must be contained within \<aop:config>.|
|\<aop:declare-parents>|	Introduces additional interfaces to advised objects that are transparently implemented.|
|\<aop:pointcut>|	Defines a Pointcut|

```java
public class Audience {
  public void silenceCellPhones() {System.out.println("Silencing cell phones");}
  public void takeSeats() { System.out.println("Taking seats");}
  public void applause() {System.out.println("CLAP CLAP CLAP!!!");}
  public void demandRefund() {System.out.println("Demanding a refund");}
}
```
```xml
<aop:config>
 <aop:aspect ref="audience">
  <aop:before pointcut="execution(** concert.Performance.perform(..))"
      method="silenceCellPhones"/>
   ….
 </aop:aspect>
</aop:config>
```

![]({{site.cdn}}/spring/spring-aop/advice-example-xml.png)

```java
public class Audience {
    public void watchPerformance(ProceedingJoinPoint jp) {
        try {
            System.out.println("Silencing phones");
            System.out.println("Taking seats");
            jp.proceed();
            System.out.println("CLAP CLAP CLAP!!!");
        } catch (Throwable e) {
            System.out.println("Demanding a refund");
        }
    }
}
```
```xml
<aop:config>
 <aop:aspect ref="audience">
 <aop:pointcut id="performance"  
     expression="execution(** concert.Performance.perform(..))" />
 <aop:around pointcut-ref="performance"
            method="watchPerformance"/>
 </aop:aspect>
</aop:config>
```
In xml, use and keyword instead of && (because ampersands are interpreted as the beginning of an entity in XML).
```xml
<aop:aspect>
   <aop:declare-parents types-matching="concert.Performance+"  
   implement-interface="concert.Encoreable" 
   default-impl="concert.DefaultEncoreable"/>
</aop:aspect>
```
```xml
<aop:aspect>
    <aop:declare-parents types-matching="concert.Performance+"
     implement-interface="concert.Encoreable"
     delegate-ref="encoreableDelegate"/>
</aop:aspect>
```

The delegate-ref attribute refers to a Spring bean as the introduction delegate. This assumes that a bean with an ID of encoreableDelegate exists in the Spring context:
```xml
<bean id="encoreableDelegate" class="concert.DefaultEncoreable" />
```
The difference between directly identifying the delegate using default-impl and indirectly using delegate-ref is that the latter will be a Spring bean that itself may be injected, advised, or otherwise configured through Spring.
