---
layout: post
title: Attribute Directives
permalink: /:collection/angular/directive/attribute
---

* Alter the appearance or behavior of an existing element.

```html
<input [(ngModel)]="hero.name">	// 2 way binding

<!-- Binds presence of css classes to the truthiness of associated map values. 
right-hand expression should return {class-name: true/false} map.-->
<div [ngClass]="{'activeClass': (isActive === 'true'), 'disabledClass': isDisabled}">

<!-- Allows you to assign styles to an HTML element using CSS. -->
<div [ngStyle]="{'backgroung-color': 'green'}">
<div [ngStyle]="{backgroundColor: getColor()}">
<div [ngStyle]="dynamicStyles()">
```
