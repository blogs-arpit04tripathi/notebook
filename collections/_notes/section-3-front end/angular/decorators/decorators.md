---
layout: post
title: Decorators
permalink: /:collection/angular/decorators
---


* Allows us to **decorate** classes and functions, similar to annotations in java 
* Functions that attaches metadata to TypeScript classes, so compiler knows what those classes mean and how they should work.

# Decorator Types
* Class decorators, e.g. `@Component` and `@NgModule`
* Property decorators for properties inside classes, e.g. `@Input` and `@Output`
* Method decorators for methods inside classes, e.g. `@HostListener`
* Parameter decorators for parameters inside class constructors, e.g. `@Inject`

| List of Decorators |                  |              |               |
| ------------------ | ---------------- | ------------ | ------------- |
| @NgModule          | @Component       | @Directive   |
| @Injectable        | @Pipe            |
| @Input             | @Output          | @HostBinding | @HostListener |
| @ContentChild      | @ContentChildren | @ViewChild   | @ViewChildren |