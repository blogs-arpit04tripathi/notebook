---
layout: post
title: Hystrix
permalink: /:collection/microservices/hystrix
---

- Open source library created by Netflix.
- Implements Circuit Breaker pattern so you don't have to.
- Hystrix is a latency and fault tolerance library.
- Designed for complex distributed systems where failure is inevitable
  - isolate points of access to remote systems, services and 3rd party libraries
  - stop cascading failure
  - enable resilience
- We will be using two features of Hystrix-
  -	Circuit Breaker
  -	Fallback method - Can return default response or cached response.
- Give it the configuration and it does the work.
  - Works well with SpringBoot.
- **References**
  - [Spring Cloud- Circuit Breaker using Netflix Hystrix Simple Example](https://www.javainuse.com/spring/spring_hystrix_circuitbreaker){:target="_blank"}
  - [Spring Cloud- Netflix Hystrix Fallback method Simple Example](https://www.javainuse.com/spring/spring_hystrix){:target="_blank"}

# Adding Hystrix to SpringBoot
- Add dependency `spring-cloud-starter-netflix-hystrix`
- `@EnableCircuitBreaker` to application class
- `@HystrixCommand` to methods that need circuit breaker.
- Configure Hystrix behavior.

If the exceptions keep on occuring in the firstPage method() then the Hystrix circuit will break and the employee consumer will skip the firtsPage method all together and directly call the fallback method.

The purpose of circuit breaker is to give time to the first page method or other methods that the firstpage method might be calling and is causing the exception to recover. It might happen that on less load the issue causing the exceptions have better chance of recovering.

```java
@HystrixCommand(fallbackMethod="getFallbackCatalog")
getCatalog(@PathVariable String userId){}

getFallbackCatalog(@PathVariable String userId){
  // parameters should be same
  // should return harcoded response or response from cache, no complicated logics here
  // Why no complicated logic? Because we don't want fallback to have exception and another fallback
}
```

![]({{site.cdn}}/webservices/microservices/hystrix-microservices.png)
	
![]({{site.cdn}}/webservices/microservices/hystrix-service-consumer.png)

![]({{site.cdn}}/webservices/microservices/hystrix-fallback.png)

![]({{site.cdn}}/webservices/microservices/hystrix-circuitbreaker.png)
