---
layout: post
title: LifeCycle Hooks
permalink: /:collection/angular/lifecycle-hooks
---


* Component lifecycle managed by Angular.
* Angular creates it, renders it, creates and renders its children, checks it when its data-bound properties change, and destroys it before removing it from the DOM.
* Angular offers lifecycle hooks that provide visibility into these key life moments and the ability to act when they occur.
* A directive has the same set of lifecycle hooks.

![lifecycle-of-directive-vs-component]({{site.cdn}}/angular/lifecycle-of-directive-vs-component.png)

### ngOnChanges()
* Respond when Angular (re)sets data-bound input properties. (@Input)
* The method receives a SimpleChanges object of current and previous property values.
* Called before ngOnInit() and whenever one or more data-bound input properties change.

```ts
export class ServerElementComponent implements onInit, onChnages{
  @Input('serverElement') element: {name: string, content:string};
  ngOnChanges(changes: SimpleChanges){
    console.log('ngOnChanges called!');
    console.log(changes);
    // SimpleChange contains @Input element
  }
}
```

### ngOnInit()	
* Initialize the directive/component after Angular first displays the data-bound properties and sets the directive/component's input properties.
* When it is Initialized but not displayed in the DOM.
* Called once, after the first ngOnChanges().
* Runs after the constructor.

### ngDoCheck()
* Detect and act upon changes that Angular can't or won't detect on its own.
* Called during every change detection run, immediately after ngOnChanges() and ngOnInit().
* Runs on every check run by angular, irrespective of any changes made.
* Very powerful tool, can be used in cases where you have to do something manually as angular didn't pick up the changes.

### ngAfterContentInit()
*	Respond after Angular projects external content into the component's view / the view that a directive is in.
*	Called only once ie. after the first ngDoCheck().
* Called after content (in ng-content) has been projected into the view.

### ngAfterContentChecked()
* Respond after Angular checks the content projected into the directive/component.
* Called after the ngAfterContentInit() and every subsequent ngDoCheck().

### ngAfterViewInit()
*	Respond after Angular initializes the component's views and child views / the view that a directive is in.
*	Called once after the first ngAfterContentChecked().

### ngAfterViewChecked()
*	Respond after Angular checks the component's views and child views / the view that a directive is in.
*	Called after the ngAfterViewInit() and every subsequent ngAfterContentChecked().

### ngOnDestroy()
*	Cleanup just before Angular destroys the directive/component. 
*	Unsubscribe Observables and detach event handlers to avoid memory leaks.
*	Called just before Angular destroys the directive/component.

![lifecycle-hooks]({{site.cdn}}/angular/lifecycle-hooks.png)

![ngOnChanges()]({{site.cdn}}/angular/ngOnChanges-example.png)
