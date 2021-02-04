---
layout: post
title: Decorator @Input()
permalink: /:collection/angular/input
---

* *Read more about [@Input](https://angular.io/api/core/Input){:target="_blank"}*
* Parent to Child communication.
* Makes property bind-able from outside the component.
* Declares an input property that you can update via property binding.
* (example: <my-cmp [myProperty]="someExpression">).
* Custom Attribute Binding

```ts
/* app-root */
<app-server-element *ngFor="let server of servers" [element]="server"></app-server-element>
<app-server-element *ngFor="let server of servers" [srvElement]="server"></app-server-element> // with alias srvElement
/* app-server-element @Component */
@Input() element: {type: string, name:string, content:string};
@Input('srvElement') element: {type: string, name:string, content:string}; // with alias srvElement
```
