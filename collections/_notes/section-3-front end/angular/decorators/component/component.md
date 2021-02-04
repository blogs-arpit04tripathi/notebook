---
layout: post
title: Decorator - @Component
permalink: /:collection/angular/component
---

```
Component = template + class (typescript)
```

root component connects a component hierarchy with the page DOM.

Template 
* combines HTML with Angular markup that can modify the HTML elements before they are displayed.
* Together, **a component and template define an Angular view**.

```ts
import { Component } from '@angular/core';
@Component({
  selector: 'app-root', // as selector
  // selector: '[app-root]', // as attribute <div app-root/>
  // selector: '.app-root', // as class <div class="app-root"/>
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'app';
}
```
