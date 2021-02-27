---
layout: post
title: Decorator - @Directive
permalink: /:collection/angular/directive
---

- Directives are instructions in the DOM to render templates.
- Directives can optionally have a template of themselves.
- @Component is also a directive, which extends the @Directive with template-oriented features.

```html
<p appTurnGreen>Receives a green background!</p>
```
```ts
@Directive({
  selector:'[appTurnGreen]'
})
export class TurnGreenDirective{
  ...
}
```

![directive]({{site.cdn}}/angular/directive.png)
