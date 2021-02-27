---
layout: post
title: Dependency Injection
permalink: /:collection/angular/dependency-injection
---

*	`@Injectable` decorator provide the metadata that allows Angular to inject it into a component as a dependency.
*	Similarly, use the @Injectable decorator to indicate that a component or other class (such as another service, a pipe, or an NgModule) has a dependency. A dependency doesn't have to be a service—it could be a function, for example, or a value.
*	Dependency injection (often called DI) is wired into the Angular framework and used everywhere to provide new components with the services or other things they need.
  -	The **injector** is the main mechanism. Angular creates an application-wide injector for you during the bootstrap process.
  -	The injector maintains a container of dependency instances that it has already created, and reuses them if possible.
  -	A provider is a recipe for creating a dependency. 
  -	For any dependency you need in your app, you must register a provider with the app's injector, so that the injector can use it to create new instances.
*	When Angular creates a new instance of a component class, it determines which services or other dependencies that component needs by looking at the types of its constructor parameters. 

```ts
constructor(private service: HeroService) { }
```

*	When Angular discovers that a component depends on a service, it first checks if the injector already has any existing instances of that service. If a requested service instance does not yet exist, the injector makes one using the registered provider, and adds it to the injector before returning the service to Angular.
*	When all requested services have been resolved and returned, Angular can call the component's constructor with those services as arguments. The process of HeroService injection looks something like this:

![dependency-injection]({{site.cdn}}/angular/dependency-injection.png)

![hierarchial-di]({{site.cdn}}/angular/hierarchial-di.png)
