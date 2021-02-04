---
layout: post
title: Debouncing Request
permalink: /:collection/angular/rxjs/debouncing-requests
---

Sending a request for every keystroke could be expensive. It's better to wait until the user stops typing and then send a request. That's easy to implement with RxJS operators.
*	debounceTime(500) - wait for the user to stop typing (1/2 second in this case).
*	distinctUntilChanged() - wait until the search text changes.
*	switchMap() - send the search request to the service.

```ts
withRefresh = false;
packages$: Observable<NpmPackageInfo[]>;
private searchText$ = new Subject<string>();

search(packageName: string) {
  this.searchText$.next(packageName);
}

ngOnInit() {
  this.packages$ = this.searchText$.pipe(
    debounceTime(500),
    distinctUntilChanged(),
    switchMap(packageName =>
      this.searchService.search(packageName, this.withRefresh))
  );
}

constructor(private searchService: PackageSearchService) { }
```
