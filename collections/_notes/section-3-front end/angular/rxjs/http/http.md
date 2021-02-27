---
layout: post
title: Http Calls using RxJs
permalink: /:collection/angular/rxjs/http
---

![rxjs-http]({{site.cdn}}/angular/rxjs-http.png)

```ts
import { HttpClientModule } from '@angular/common/http';
@NgModule(
{ imports: [// import HttpClientModule after BrowserModule.
   HttpClientModule, 
],
//Component
showConfig() {
  this.configService.getConfig()
    .subscribe(
      (data: Config) => this.config = {
        heroesUrl: data['heroesUrl'],
        textfile:  data['textfile']
       }, // success path
      (error) => this.error = error // error path
     );
}
```
```ts
//Json
{ "heroesUrl": "api/heroes", "textfile": "assets/textfile.txt" }
```
```ts
//Service
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
@Injectable()
export class ConfigService {
  constructor(private http: HttpClient) { }
  configUrl = 'assets/config.json';
  getConfig() {   return this.http.get(this.configUrl); }
  //return this.http.get<Config>(this.configUrl);  //Observable
}
```
```ts
//Config structure
export interface Config {
  heroesUrl: string;
  textfile: string;
}
```
