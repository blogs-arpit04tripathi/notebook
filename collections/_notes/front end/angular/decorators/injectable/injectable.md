---
layout: post
title: Decorator - @Injectable
permalink: /:collection/angular/injectable
---

* Both components and services are simply classes, with decorators that mark their type and provide metadata that tells Angular how to use them.
* `@Injectable` decorator provides the metadata that allows your service to be injected into client components as a dependency.
* For data or logic that is not associated with a specific view, and that you want to share across components.
* Dependency injection (or DI) lets you keep your component classes lean and efficient. components don't fetch data from the server, validate user input, or log directly to the console; they delegate such tasks to services.
* Template, component and services are loosely coupled and have separation of concerns.
* Services can depend on other services.

```ts
import { Injectable } from '@angular/core';
@Injectable({
  providedIn: 'root',
})
export class HeroService { 
private heroes: Hero[] = []; 
constructor( private backend: BackendService, private logger: Logger) {} 
getHeroes() { 
  this.backend.getAll(Hero)
  .then((heroes: Hero[])=>{this.logger.log(`Fetched ${heroes.length} heroes.`); 
  this.heroes.push(...heroes); // fill cache }); 
  return this.heroes; }
}
```
