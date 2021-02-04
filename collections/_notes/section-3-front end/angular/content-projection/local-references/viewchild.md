---
layout: post
title: Decorator @ViewChild()
permalink: /:collection/angular/viewchild
---

- Can get access to any local reference or any other element directly from the ts code.
- Earlier we passed local reference to method, but sometimes you may need to get the element before method call.
- Type is `ElementRef`
@ViewChild(myPredicate) myChildComponent;
* [@ViewChild](https://angular.io/api/core/ViewChild)
* Binds the first result of the component view query (myPredicate) to a property (myChildComponent) of the class. Not available for directives.
* The same change (add { static: true } as a second argument) needs to be applied to ALL usages of @ViewChild() (and also @ContentChild(), IF you plan on accessing the selected element inside of ngOnInit().
* If you DON'T access the selected element in ngOnInit (but anywhere else in your component), set static: false instead!
* Can be accessed only after View Init.
* Here, you access something from a child component in your view.

```html
<!-- Normal definition -->
<input type="text" class="form-control" [(ngModel)]="newServerContent">
<!-- Element to be accessed as view child -->
<input type="text" class="form-control" #serverNameInput>
<!-- app-root.ts -->
<!-- by selector -->
@ViewChild('serverNameInput', {static: true}) serverNameInput: ElementRef; 
<!-- by component name -->
<!-- Gets First Element of that component type -->
@ViewChild(ServerCreatorComponent, {static: true}) serverNameInput: ElementRef;
var text = this.serverNameInput.nativeElement.value;
<!-- can be used to modify DOM and output data like below, but not recommended. -->
<!-- Instead use String interpolation or property binding to output the data. -->
this.serverNameInput.nativeElement.value = "new value";
```

