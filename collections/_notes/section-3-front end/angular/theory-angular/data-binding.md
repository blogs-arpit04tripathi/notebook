---
layout: post
title: Data Binding
permalink: /:collection/angular/data-binding
---


- binding component ts data to its template.
- **Interpolation** - Angular evaluates all expressions in double curly braces, converts the expression results to strings, and links them with neighboring literal strings. Finally, it assigns this composite interpolated result to an element or directive property.
- Angular processes all data bindings once per JavaScript event cycle, from the root of the application component tree through all child components.

|Data Binding||
|---|---|
|String Interpolation|`<li>{ {hero.name}}</li>`|
|property binding|`<app-hero-detail [disabled]="!isEnabled()"></app-hero-detail>`|
|event binding|`<li (click)="selectHero(hero)"></li>`|
|2-way binding|`<input [(ngModel)]="hero.name">`, requires FormsModule for ngModel directive.|
|Class Binding|`[class.active = “isActive”]`|
|Style Binding|[style.*]|

![]({{site.cdn}}/angular/data-binding.png)

![]({{site.cdn}}/angular/data-bindings.png)

```
<input type="text" class="form-control" (input)="onUpdateServerName($event)">
<p>{ {serverName}}</p>

onUpdateServerName(event:Event){
  this.serverName = (<HTMLInputElement>event.target).value;
}
```

## Custom Binding
1. **Custom Attribute Binding** - `@Input()` to pass attribute from parent to child
2. **Custom Event Binding** - `@Output()` to pass attribute from child to parent