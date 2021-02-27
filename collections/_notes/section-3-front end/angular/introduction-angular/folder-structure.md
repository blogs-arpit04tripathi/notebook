---
layout: post
title: Folder Structure
permalink: /:collection/angular/folder-structure
---

# Folder Structure

- [understanding folder structure](https://overflowjs.com/posts/Angular-8-Understanding-Directory-Structure-and-Creating-CRUD-App){:target="_blank"}
- [Structure](https://www.c-sharpcorner.com/blogs/folder-structure-of-angular-5-project){:target="_blank"}

![folder-structure]({{site.cdn}}/angular/folder-structure.png)

**package.json**
- scripts
  - `ng serve` - Angular deployment live server is angular’s inhouse server and it looks for index.html on startup.
- dependencies (***npm install*** added here)
- devDependencies

![package-json]({{site.cdn}}/angular/package-json.png)

**angular.json**
- bootstrapping (image on below page)
- build configs of project architect
  - bootstrap, jquery and popper
  - aot flag

![angular-json]({{site.cdn}}/angular/angular-json.png)

* index.html
  - file that hosts your bootstrap component and its hierarchy
* app.module.ts :
  - @NgModule
  - declarations – AppComponent, available for use to other components of this module without any import
  - imports – BrowserModule, AppRoutingModule, other modules
  - exports – components exported to other modules.
  - bootstrap – AppComponent, 1st component to be launched as it is available for index.html.
  - providers – service, pipe, validator

export classs MyComp{ } : `export` tells the module that it is available and can be imported to use.

* Webpack Configuration files: The webpack.conf.js is at the root of the project. It branches to three more configuration files
  - webpack.dev.js
  - webpack.prod.js
  - webpack.common.js.
* Use the start script to run webpack dev server using dev configuration. 

```
"scripts": {
     "start": "webpack-dev-server --inline --progress --port 8080",
```

* Webpack creates three bundles, with the application bundled into app.js

```
entry: {
 'polyfills': './src/polyfills.ts',
 'vendor': './src/vendor.ts',
 'app': './src/main.ts'
},
```
