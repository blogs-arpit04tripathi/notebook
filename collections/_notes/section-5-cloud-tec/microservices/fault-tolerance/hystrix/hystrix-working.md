---
layout: post
title: How does Hystrix Work?
permalink: /:collection/microservices/hystrix/working
---

Creates a Hystrix Proxy object.

![]({{site.cdn}}/webservices/microservices/hystrix-proxy.png)

For Movie Catalog API Ecosystem, we should not put @HystrixCommand on getUserMovieRatingCatalog(userId) method but on getRatings and getMovieInfo methods, Why?
- **Case 1**
  - get ratings is failing, but get movie info is working
  - take default response of ratings response and call the working movie info service
- **Case 2**
  - get ratings is working, get movie info is failing
  - take response from get ratings and default response from get movie info
  - It is acceptable to get all movie ratings with few movies missing details due to default response.

Here, even if you refractor the code to make these 2 calls as separate methods we will get error due to Hystrix Proxy Class.
- When there is a bean with annotations like @HystrixCommand, we are holding the Proxy instance of the class rather than the actual instance.
- This Proxy instance intercepts the call.

**What changed by refactoring**
- Before refactoring, @HystrixCommand on getUserMovieRatingCatalog
  - Spring Framework was calling the method on the Hystrix Proxy instance hence Hystrix was able to intercept the call and execute the fallback method.
- On refactoring
  - @HystrixCommand methods are being called from a method inside the hystrix proxy instance, hence Hystrix has no say to intercept the call here.
  - Solution - Move the methods to a separate bean class so that getUserMovieRatingCatalog calls these methods on hystrix proxy object and fallback method works fine.
