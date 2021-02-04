---
layout: post
title: Angular Installation
permalink: /:collection/angular/installation
---

# Installation
* Download [node](https://nodejs.org/en/)
* Environment variable – pointing to node folder
* Download Visual Studio and got to empty folder
* open console (ctrl+`)

# Command Line instructions
* saves time and makes it easy for development process by making scaffolding for components, services, routing etc.
* **Scaffold** – component, directive, pipe, service, class, guard, interface, enum, module
* `ng new projectName --skip-install`
  - --skip-install is used to avoid that npm dependencies are installed automatically.

**Install angular cli**
```
node –v 
npm –v
npm install –g @angular/cli@latest
ng –-version
```
```
npm i underscore -g
npm uninstall -g @angular/cli@latest
npm cache clean
```
**create single project workspace**
```
ng new <project> --skip-install
cd <project>
```
**create multi-project workspace**
```
ng new my-workspace --skip-install --createApplication="false"
cd my-workspace
ng generate application my-first-app
```
**adding bootstrap4**
```
// --save ==> updates package.json with dependency
npm install jquery@latest popper.js@latest bootstrap@latest --save
// now, you need to manually add entry to angular.json styles and scripts
npm install bootstrap@latest ngx-bootstrap@latest --save
```
**generate commands**
```
ng g c <component-name>
ng g directive my-new-directive 
ng g pipe my-new-pipe 
ng g service my-new-service 
ng g class my-new-class 
ng g guard my-new-guard 
ng g interface my-new-interface 
ng g enum my-new-enum 
ng g module my-module
```
```
npm start (calls ng serve automatically)
npm config set https-proxy <proxy>
npm config set http-proxy <proxy>
ng serve
ng generate
ng build – dist file
ng lint – check coding standards
ng test
```