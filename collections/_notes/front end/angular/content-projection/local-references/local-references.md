---
layout: post
title: Using Local References in Templates
permalink: /:collection/angular/local-references
---

- Can be used only in template, not in typescript.
- Type is `HTMLInputElement`

```html
<!-- Normal definition -->
<input type="text" class="form-control" [(ngModel)]="newServerContent">
<!-- Local References -->
<input type="text" class="form-control" #serverNameInput>
<button class="btn btn-primary" (click)="onAddServer(serverNameInput)">Add Server</button>
<!-- app-root.ts -->
onAddServer(serverNameInput: HTMLInputElement){
  console.log(serverNameInput.value);
}
```
