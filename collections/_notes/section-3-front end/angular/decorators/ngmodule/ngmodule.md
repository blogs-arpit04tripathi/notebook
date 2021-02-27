---
layout: post
title: Decorator - @NgModule
permalink: /:collection/angular/ngmodule
---

![modules]({{site.cdn}}/angular/modules-app-diagram.png)

* Angular app is a set of NgModules.
* declares a compilation context for closely related set of capabilities.
* By default **AppModule (app.module.ts)** is the root module from where bootstrapping happens.
* Distinct functional modules helps with reusability and *lazy-loading* (minimize amount of code to be loaded at startup)

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { HttpClientModule } from '@angular/common/http';
import { AppComponent } from './app.component';
@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule,  FormsModule, HttpClientModule ],
  exports:[],
  entryComponents: [SomeComponent, OtherComponent],
  providers: [Service, Pipes],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

**providers**
* global collection of services accessible in all parts of app. 
* You can also specify providers at the component level, which is often preferred.

**bootstrap**
* root component, which hosts all other app views. Only the root NgModule should set this property.

**declarations** 
* components, [directives](https://angular.io/guide/attribute-directives) and [pipes](https://angular.io/guide/pipes)
* declared classes are visible within the module but invisible to components in a different module unless they are exported from this module and the other module imports this one.

| NgModule | Import from | Why use it |
|---|---|---|
| [BrowserModule](https://angular.io/api/platform-browser/BrowserModule)  | @angular/platform-browser | When you want to run your app in a browser|
| [CommonModule](https://angular.io/api/common/CommonModule)              | @angular/common           | When you want to use [NgIf](https://angular.io/api/common/NgIf), NgFor|
| [FormsModule](https://angular.io/api/forms/FormsModule)                 | @angular/forms            | When you want to build template driven forms (includes [NgModel](https://angular.io/api/forms/NgModel))   |
| [ReactiveFormsModule](https://angular.io/api/forms/ReactiveFormsModule) | @angular/forms            | When you want to build reactive forms|
| [RouterModule](https://angular.io/api/router/RouterModule)              | @angular/router           | When you want to use [RouterLink]( https://angular.io/api/router/RouterLink), .forRoot(), and .forChild() |
| [HttpClientModule](https://angular.io/api/common/http/HttpClientModule) | @angular/common/http      | When you want to talk to a server|
