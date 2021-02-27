---
layout: post
title: JIT vs AOT
permalink: /:collection/angular/jit-vs-aot
---


The main differences between JIT and AOT in Angular are:
*	The time when the compilation takes place.
*	JIT generates JavaScript however, AoT usually generates TypeScript.
* `ng build` command creates a dist folder with deployables.

```ts
ng build --prod --jit
ng build --prod --aot
```

![jit-vs-aot.png]({{site.cdn}}/angular/jit-vs-aot.png)
![jit-vs-aot.png-points]({{site.cdn}}/angular/jit-vs-aot-points.png)
![jit-vs-aot.png-flow]({{site.cdn}}/angular/jit-vs-aot-flow.png)


# Flow of events with Just-in-Time Compilation
*	Development of Angular application with TypeScript.
*	Compilation of the application with tsc.
*	Bundling.
*	Minification.
*	Deployment.

Once we’ve deployed the app and the user opens her browser, she will go through the following steps (without strict CSP):
-	Download all the JavaScript assets.
-	Angular bootstraps.
-	Angular goes through the JiT compilation process, i.e. generation of JavaScript for each component in our application.
The application gets rendered.


# Flow of events with Ahead-of-Time Compilation
In contrast, with AoT we get through the following steps:
*	Development of Angular application with TypeScript.
*	Compilation of the application with ngc.
*	Performs compilation of the templates with the Angular compiler and generates (usually) TypeScript.
*	Compilation of the TypeScript code to JavaScript.
*	Bundling.
*	Minification.
*	Deployment.

Although the above process seems lightly more complicated the user goes only through the steps:
*	Download all the assets.
*	Angular bootstraps.
* The application gets rendered.
