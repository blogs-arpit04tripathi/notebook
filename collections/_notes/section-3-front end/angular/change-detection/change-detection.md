---
layout: post
title: Change Detection
permalink: /:collection/angular/change-detection
---

* Change Detection means updating the DOM every time the data is changed.
* A model in Angular can change as a result of one of the following scenarios:
  -	DOM events (click, hover over, etc.)
  -	AJAX requests
  -	Timers (setTimer(), setInterval())
*	All angular applications consist of a hierarchical tree of components. At runtime, Angular creates a change detector class separately for each tree component, which then eventually forms a hierarchy of change detectors similar to the hierarchy tree components.
*	When change tracking is activated, Angular goes through this tree of change detectors to determine if any of them have changed.
*	The change detection cycle is always performed once for each detected change and starts from the root change detector and is sequentially reduced. 

```ts
import { Component, OnInit, Input , ChangeDetectionStrategy } from '@angular/core';
@Component({
  selector: 'app-message',
  changeDetection: ChangeDetectionStrategy.OnPush,
  templateUrl: ‘’
})
export class MessageComponent implements OnInit {
  @Input() company;
  constructor() { }
  ngOnInit() {  }
}
```

![change-detector-hierarchy]({{site.cdn}}/angular/change-detector-hierarchy.png)
