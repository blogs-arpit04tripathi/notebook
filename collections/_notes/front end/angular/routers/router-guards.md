---
layout: post
title: Router Guards
permalink: /:collection/angular/routers/guards
---

> Read full article on [Router Guards](https://codecraft.tv/courses/angular/routing/router-guards/) here.

* To check permissions and return a 403 error page if the user didn’t have permissions, or perhaps redirect them to a login/register page if they were not signed up. with Router Guards we can use this functionality.
* 403 is a HTTP error code - Permission Denied
* For a given route we can implement zero or any number of Guards.

**Use Cases**
- Maybe the user must login (authenticate) first.
- Perhaps the user has logged in but is not authorized to navigate to the target component.
- We might ask the user if it’s OK to discard pending changes rather than save them.
