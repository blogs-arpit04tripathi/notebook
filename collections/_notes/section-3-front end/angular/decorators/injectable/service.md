---
layout: post
title: Providing services
permalink: /:collection/angular/service
---

* You must register at least one provider of any service you are going to use. You can register providers in modules or in components.
*	When you add providers to the root module, the same instance of a service is available to all components in your app.
*	When you register a provider at the component level, you get a new instance of the service with each new instance of that component.

```ts
providers: [ BackendService, HeroService, Logger ],
@Component({
 	selector: 'app-hero-list', 
	templateUrl: './hero-list.component.html', 
	providers: [ HeroService ] 
})
```
