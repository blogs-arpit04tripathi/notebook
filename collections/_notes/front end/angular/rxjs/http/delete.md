---
layout: post
title: Delete Request
permalink: /:collection/angular/rxjs/http/delete
---

```ts
/** DELETE: delete the hero from the server */
deleteHero (id: number): Observable<{}> {
  const url = `${this.heroesUrl}/${id}`; // DELETE api/heroes/42
  return this.http.delete(url, httpOptions)
    .pipe(
      catchError(this.handleError('deleteHero'))
    );
}
```
```ts
this.heroesService.deleteHero(hero.id).subscribe();
```

* An HttpClient method does not begin its HTTP request until you call subscribe() on the observable returned by that method. This is true for all HttpClient methods.
