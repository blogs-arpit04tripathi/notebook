---
layout: post
title: Post Request
permalink: /:collection/angular/rxjs/http/post
---

```ts
/** POST: add a new hero to the database */
addHero (hero: Hero): Observable<Hero> {
  return this.http.post<Hero>(this.heroesUrl, hero, httpOptions)
    .pipe(
      catchError(this.handleError('addHero', hero))
    );
}
```
```ts
import { HttpHeaders } from '@angular/common/http';
const httpOptions = {
  headers: new HttpHeaders({
    'Content-Type':  'application/json',
    'Authorization': 'my-auth-token'
  })
};
```
```ts
this.heroesService.addHero(newHero).subscribe(hero => this.heroes.push(hero));
```
