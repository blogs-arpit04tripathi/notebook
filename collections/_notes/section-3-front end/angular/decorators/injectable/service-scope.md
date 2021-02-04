---
layout: post
title: Change Scope of Service
permalink: /:collection/angular/service-scope
---

***How to change Scope of Service? or make it singleton?***

```ts
// Option 1
providers: [ { provide: MyService, singleton: true  } ],
or
providers: [ { provide: MyService, scope: 'singleton'  } ],
```
```ts
// Option 2
@Injectable({ singleton: true })
export class MyserviceService {
  constructor() { }
}
```
```ts
// Option 3
@Injectable({ scope: 'singleton' })
export class MyserviceService {
  constructor() { }
}
```
