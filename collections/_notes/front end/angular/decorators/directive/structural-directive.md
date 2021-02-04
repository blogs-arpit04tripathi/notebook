---
layout: post
title: Structural Directives
permalink: /:collection/angular/directive/structural
---

Alter layout structure by adding, removing, and replacing elements in DOM.

```html
<p *ngIf="heroSelected; else heroNotSelected">You have selected a hero - { {hero}}</p>
<ng-template #heroNotSelected>
  <p>No hero selected.</p>
</ng-template>
```

```html
if (foo === 1) {
  ...
} else if (bar === 99) {
  ...
} else if (foo === 2) {
  ...
} else {
  ...
}
```

```html
<ng-container *ngIf="foo === 1; else elseif1">foo === 1</ng-container>
<ng-template #elseif1>
    <ng-container *ngIf="bar === 99; else elseif2">bar === 99</ng-container>
</ng-template>
<ng-template #elseif2>
    <ng-container *ngIf="foo === 2; else else1">foo === 2</ng-container>
</ng-template>
<ng-template #else1>else</ng-template>
```

```html
<li *ngFor="let hero of heroes; let i = index">
  <a href=hero.url>i - {{hero.name}}</a>
</li>
```

```html
<div [ngSwitch]="conditionExpression">
 	<ng-template [ngSwitchCase]="case1Exp">...</ng-template>
 	<ng-template ngSwitchCase="case2LiteralString">...</ng-template>
 	<ng-template ngSwitchDefault>...</ng-template>
</div>
```
