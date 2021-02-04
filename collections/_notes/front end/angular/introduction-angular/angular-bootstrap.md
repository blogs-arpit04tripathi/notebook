---
layout: post
title: How Angular App Bootstraps
permalink: /angular/bootstrap
---

1. main.ts ==> `platformBrowserDynamic().bootstrapModule(AppModule)`
2. AppModule ==> `@NgModule({... bootstrap: [AppComponent]})`
3. AppComponent ==> Will host all other custom components created
