---
layout: post
title: Defining an aspect
permalink: /:collection/spring/aop/defining-aspects
---

```java
@Configuration
@EnableAspectJAutoProxy
@ComponentScan
public class ConcertConfig {
 @Bean
 public Audience audience() { return new Audience(); }
}
```

- We use AspectJ annotations, but it is still Spring’s proxy-based aspects.
  - we are still limited to proxying method invocations.
- **@Aspect** - Defines Aspect class. 
-	**@Pointcut** - reusable pointcut within an @Aspect aspect.
- **@AfterThrowing**
  - We are only reading the exception, exception will propogate as usual.
  - If you want to stop the exception propogation, use **@Around** advice.
- **@After**
  - works as finally method, will run on completion of advised method.
  - @After doesn't have access to exception thrown, u will need to use @AfterThrowing in that case.
  - @After will run after the @AfterThrowing or @AfterReturning.
- **@Around**
  - can be used to measure execution time.
  - wraps the advised method - (before + after) advice in a single advice method.
  - **ProceedingJoinPoint**
    - mandatory parameter
    - to invoke the advised method from within your advice.
    - to pass control to the advised method, call ProceedingJoinPoint’s proceed().
    - Use Cases
      - You can omit a proceed() method to block access to the advised method
      - You can invoke it multiple times, say, to implement retry logic.

```java
package concert;

import org.aspectj.lang.annotation.AfterReturning;
import org.aspectj.lang.annotation.AfterThrowing;
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.aspectj.lang.annotation.Pointcut;

@Aspect
public class Audience {

    @Pointcut("execution(** concert.Performance.perform(..))")
    public void performance() {}

    @Pointcut("execution(** concert.Performance.get*(..))")
    public void getter() {}

    @Pointcut("execution(** concert.Performance.set*(..))")
    public void setter() {}
    // combining pointcuts Using AspectJ Expression
    @Pointcut("performance() && !(getter() || setter())")
    public void performanceNoGetterSetter() {}

    @Before("performance()") // using pointcut rather than expression
    @Before("execution(** concert.Performance.perform(..))") // using aspectj expression
    public void silenceCellPhones() {
        System.out.println("Silencing cell phones");
    }

    @Before("performance()")
    public void takeSeats(JoinPoint joinPoint) {
        System.out.println("Taking seats");
        MethodSignature mSign = (MethodSignature) joinPoint.getSignature(); // get method signature
        System.out.println("Method : " + mSign);
        Object[] args = joinPoint.getArgs(); // get method arguments
        for (Object arg: args)
            System.out.println(arg);
    }

    @AfterReturning(pointcut = "performance()", returning = "response")
    public void applause(JoinPoint joinPoint, List < Account > response) {
        // AfterReturning with response object
        System.out.println("CLAP CLAP CLAP!!!");
    }

    @AfterThrowing(pointcut = "performance()", throwing = "exception")
    public void demandRefund(JoinPoint joinPoint, Throwable exception) {
        System.out.println("Demanding a refund");
    }

    @After("performance()")
    public void takeSeats(JoinPoint joinPoint) {
        System.out.println("Perforamnce is complete.");
    }

    @Around("performance()")
    public void watchPerformance(ProceedingJoinPoint jp) {
        try {
            System.out.println("Silencing cell phones");
            System.out.println("Taking seats");
            jp.proceed();
            System.out.println("CLAP CLAP CLAP!!!");
        } catch (Throwable e) {
            System.out.println("Demanding a refund");
        }
    }
}
```
```java
private Map < Integer, Integer > trackCounts = new HashMap < Integer, Integer > ();

@Pointcut("execution(* soundsystem.CompactDisc.playTrack(int)) && args(trackNumber)")
public void trackPlayed(int trackNumber) {}

@Before("trackPlayed(trackNumber)")
public void countTrack(int trackNumber) {
    trackCounts.put(trackNumber, getPlayCount(trackNumber) + 1);
}

public int getPlayCount(int trackNumber) {
    return trackCounts.containsKey(trackNumber) ? trackCounts.get(trackNumber) : 0;
}
```
