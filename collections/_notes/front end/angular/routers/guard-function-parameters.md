---
layout: post
title: Guard Function Parameters
permalink: /:collection/angular/routers/guards/function-parameters
---

To help determining whether or not a guard should accept or deny access the guard function can be passed certain arguments:
* **component**: Component this is the component itself.
* **route**: ActivatedRouteSnapshot — this is the future route that will be activated if the guard passes, we can use it’s params property to extract the route params.
* **state**: RouterStateSnapshot — this is the future RouterState if the guard passes, we can find the URL we are trying to navigate to from the url property.

```ts
class UnsearchedTermGuard implements CanDeactivate<SearchComponent> {
  canDeactivate(component: SearchComponent, route: ActivatedRouteSnapshot, state: RouterStateSnapshot): boolean {
    console.log(route.params);
    console.log(state.url);
    return component.canDeactivate() || window.confirm("Are you sure?");
  }
}
```

* CanDeactivate interface is a generic interface.
* Guard functions can return either a boolean or an Observable<boolean> or Promise<boolean> which resolves to a boolean at some point in the future.

Firstly lets create a function called canDeactivate on our SearchComponent, it should be the component that decides whether or not it has unsaved changes.

```ts
canDeactivate() {
  return this.itunes.results.length > 0;
}
```
