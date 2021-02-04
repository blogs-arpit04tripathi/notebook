---
layout: post
title: Decorator @Output()
permalink: /:collection/angular/output
---


@Output() myEvent = new EventEmitter();
* [@Output()](https://angular.io/api/core/Output){:target="_blank"}
* [Event Emitter](https://angular.io/api/core/EventEmitter){:target="_blank"}
* Declares an output property that fires events that you can subscribe to with an event binding.
* (example: <my-cmp (myEvent)="doSomething()">).
* Custom Event Binding.

```ts
/* app-root */
<app-server-creator (onServerCreated)="onServerAdded($event)"></app-server-creator>
<app-server-creator (onServerCreatedAlias)="onServerAdded($event)"></app-server-creator> // with alias
```
```ts
/* app-root @Component*/
onServerAdded(serverData: {name:string, content:string}){
  this.serverElement.push({
    type: 'server',
    name: serverData.name,
    content: serverData.content
  });
}
```
```ts
/* app-server-creator */
@Output() onServerCreated = new EventEmitter<{name:string, content:string}>();
@Output('onServerCreatedAlias') onServerCreated = new EventEmitter<{name:string, content:string}>(); // with alias
newServerName = '';
newServerContent = '';
onCreateServer(){
  this.onServerCreated.emit({
    name: this.newServerName,
    content: this.newServerContent
  });
}
```
