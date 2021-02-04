---
layout: post
title: Angular 8 Introduction
permalink: /:collection/angular/introduction
---

* JS Framework to create reactive SPAs.
  * for building client application (primarily browser-based) using Component Based Design Pattern.
  * **SPA** – *Single Page Application* – On click of link, no page change only the component is changed.
* Transcompiler - for [typescript](www.typescriptlang.org) to javascript
    - [babeljs.io](https://babeljs.io/) - https://babeljs.io/
* Task Managers 
    – They are just like event managers.
    - preferred options: Grunt, gull, webpack (webpack used for angular, this has babel transcompiler)
* webpack
  - open-source JavaScript module bundler.
  - made primarily for JavaScript, but it can transform front-end assets like HTML, CSS, and images if the corresponding loaders are included.
  - webpack takes modules with dependencies and generates static assets representing those modules.
  - main purpose is to bundle JavaScript files for usage in a browser.
  - example - you define styles and scripts in angular.json, they are included on \<head> automatically.
* angular-cli
    - Handles dev to deployment, debugging to testing
    - needs nodejs
    - contains webpack
