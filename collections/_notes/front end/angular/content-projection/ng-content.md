---
layout: post
title: ng-content
permalink: /:collection/angular/ng-content
---

- contents passed within the ng component selectors are projected in the component view.
- Can be used to make reusable widgets like tab widget.

```html
<!-- anything passed within the element is ignored, and no error msg is shown -->
<app-server-element></app-server-element>

<app-server-element>
  <p *ngIf="serverAdded.type === ''server">serverAdded.name</p>
</app-server-element>
<!-- app-server-element.html -->
<div>
  <ng-content></ng-content>
</div>
```

