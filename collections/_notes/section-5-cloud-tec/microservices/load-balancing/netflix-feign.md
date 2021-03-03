---
layout: post
title: Netflix Feign - Declarative REST Client
permalink: /:collection/microservices/load-balancing/netflix-feign
---

- [Netflix Feign - Declarative REST Client](https://cloud.spring.io/spring-cloud-netflix/multi/multi_spring-cloud-feign.html){:target="_blank"}


- Feign is a declarative web service client. It makes writing web service clients easier.
- Spring Cloud integrates Ribbon and Eureka to provide a load balanced http client when using Feign.
- group `org.springframework.cloud` and artifact id `spring-cloud-starter-openfeign`.

```java
@SpringBootApplication
@EnableFeignClients
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

```java
@FeignClient("stores")
public interface StoreClient {

    @RequestMapping(method = RequestMethod.GET, value = "/stores")
    List<Store> getStores();

    @RequestMapping(method = RequestMethod.POST, value = "/stores/{storeId}", consumes = "application/json")
    Store update(@PathVariable("storeId") Long storeId, Store store);
}
```

**What is Netflix Feign? What are its advantages?**  
Feign is a java to http client binder inspired by Retrofit, JAXRS-2.0, and WebSocket. Feign's first goal was reducing the complexity of binding Denominator uniformly to http apis regardless of restfulness. Previous examples in the employee-consumer we consumed the REST services exposed by the employee-producer using **REST Template**.

![]({{site.cdn}}/webservices/microservices/netflix-feign.png)

But we had to write a lot of code to perform following-
-	For Load balancing using Ribbon.
-	Getting the Service instance and then the Base URL.
-	Make use of the REST Template for consuming service.

The previous code was as below
```java
@Controller
public class ConsumerControllerClient {	
	@Autowired
	private LoadBalancerClient loadBalancer;
	
	public void getEmployee() throws RestClientException, IOException {		
		ServiceInstance serviceInstance=loadBalancer.choose("employee-producer");		
		System.out.println(serviceInstance.getUri());		
		String baseUrl=serviceInstance.getUri().toString();		
		baseUrl=baseUrl+"/employee";		
		RestTemplate restTemplate = new RestTemplate();
		ResponseEntity<String> response=null;
		try{
			response=restTemplate.exchange(baseUrl, HttpMethod.GET, getHeaders(),String.class);
		}catch (Exception ex){
			System.out.println(ex);
		}
		System.out.println(response.getBody());
	}
```

The previous code, there are chances of exceptions like NullPointer and is not optimal. We will see how the call is made much easier and cleaner using Netflix Feign. If the Netflix Ribbon dependency is also in the classpath, then Feign also takes care of load balancing by default.

> [Spring Cloud- Netflix Feign Simple Example](https://www.javainuse.com/spring/spring-cloud-netflix-feign-tutorial)
