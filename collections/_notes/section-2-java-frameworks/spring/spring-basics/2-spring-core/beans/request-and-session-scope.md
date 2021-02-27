---
layout: post
title: Working with request and session scope
permalink: /:collection/spring/bean-scopes/request-and-session-scope
---

-	In a web app, you may need to instantiate a bean that’s shared within the scope of a request or session. 

**Example** - shopping cart bean of a user in a e-commerce application
-	If singleton, then all users will be adding products to the same cart. 
-	If prototype-scoped, then products added to cart in one area of the application may not be available in another part of the application where a different prototype-scoped shopping cart was injected.
-	In the case of a shopping cart bean, session scope makes the most sense, because it’s most directly attached to a given user.

```java
@Component
@Scope(value=WebApplicationContext.SCOPE_SESSION, proxyMode=ScopedProxyMode.INTERFACES)
public ShoppingCart cart() { ... }
```
-	This tells Spring to create an instance of the ShoppingCart bean for each session in a web application. 
-	There will be multiple instances of the ShoppingCart bean, but only one will be created for a given session.
- **@Scope** also has a proxyMode attribute set to **ScopedProxyMode.INTERFACES**.
  - This attribute addresses a problem encountered when injecting a session- or request-scoped bean into a singleton-scoped bean.

```java
@Component
public class StoreService {
  @Autowired
  public void setShoppingCart(ShoppingCart shoppingCart) {
    this.shoppingCart = shoppingCart;
  }
  ...
}
```

![scoped-proxies]({{site.cdn}}/spring/spring-core/scoped-proxies.png)

-	StoreService singleton bean created when Spring application context is loaded. 
- Upon creation, Spring will attempt to inject ShoppingCart into the setShoppingCart() method.
- But ShoppingCart bean being session scoped, doesn’t exist yet.
  - There won’t be an instance of ShoppingCart until a user comes along and a session is created.
- Moreover, there will be many instances of ShoppingCart: one per user.
  - You don’t want Spring to inject just any single instance of ShoppingCart into StoreService.
  - You want StoreService to work with the ShoppingCart instance for whichever session happens to be in play when StoreService needs to work with the shopping cart.
- Instead of injecting the actual ShoppingCart bean into StoreService, Spring should inject a proxy to the ShoppingCart bean.
  - This proxy will expose the same methods as ShoppingCart so that for all StoreService knows, it is the shopping cart.
  - But ***when StoreService calls methods on ShoppingCart, the proxy will lazily resolve it and delegate the call to the actual session-scoped ShoppingCart bean***.
  - **Scoped Proxy**
- proxyMode is set to **ScopedProxyMode.INTERFACES**
  - indicating that the ***proxy should implement*** the ShoppingCart **interface** and delegate to the implementation bean.
  - interface-based proxy.
  - This is fine (and the most ideal proxy mode) as long as ShoppingCart is an interface and not a class.
- proxyMode set to **ScopedProxyMode.TARGET_CLASS**
  - to indicate that the proxy should be generated as an extension of the target class.
  - class-based proxy.
  - when ShoppingCart is a concrete class, there’s no way Spring can create an interface-based proxy.

Request-scoped beans pose the same wiring challenges as session-scoped beans. Therefore, request-scoped beans should also be injected as scoped proxies.

# Declaring scoped proxies in XML
```xml
<bean id="cart" class="com.myapp.ShoppingCart" scope="session"> 
    <aop:scoped-proxy proxy-target-class="false" />
</bean>
```
-	By default, \<aop:scoped-proxy> uses CGLib to create a target class proxy.

