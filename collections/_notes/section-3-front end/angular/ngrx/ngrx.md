---
layout: post
title: NgRx
permalink: /:collection/angular/ngrx
---


>Read more about ngrx
>* [Angular: NGRX a clean and clear Introduction](https://medium.com/frontend-fun/angular-ngrx-a-clean-and-clear-introduction-4ed61c89c1fc) 
>* [Angular Service Layers: Redux, RxJs and Ngrx Store - When to Use a Store And Why?](
https://blog.angular-university.io/angular-2-redux-ngrx-rxjs/)

* NGRX, Reactive State for Angular.
* NGRX is a group of libraries.
* NGRX <-- Redux pattern <-- Flux pattern. 
* The main purpose of this pattern is to provide a predictable state container, based on three main principles.
    - **Single source of truth** - state of your whole application is stored in an object tree within a single store.
    - **State is read-only** – you are never going to change the state directly instead you are going to dispatch actions. These actions describe what’s happening (can be things like getting, adding, removing, updating the state).
    - **Changes are made with pure functions** - reducers (remember that they are just pure functions) receive an action and the state, depending on the action dispatched (usually with a switch statement) they execute an operation and return a new state object.
* State in a redux app is immutable. So, when a reducer changes something in the state, it returns a new state object.
* pure functions – for same arguments you are going to get the same result.

***The main benefit, in my opinion, is that by binding all our components inputs to state properties we can change the change detection strategy to on push, and this is going to be a boost on performance for the application.***

![ng-rx-state-diagram]({{site.cdn}}/angular/ngrx-state-diagram.png)

![ngrx-code-action]({{site.cdn}}/angular/ngrx-code-action.png)
![ngrx-code-reducer]({{site.cdn}}/angular/ngrx-code-reducer.png)
