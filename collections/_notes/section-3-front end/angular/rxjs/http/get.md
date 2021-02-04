---
layout: post
title: Get Request
permalink: /:collection/angular/rxjs/http/get
---

* The HttpClient.get() method parsed the JSON server response into the anonymous Object type. It doesn't know what the shape of that object is.
* You can tell HttpClient the type of the response to make consuming the output easier and more obvious. get<Config>

# Reading the full response
The response body doesn't return all the data you may need. Sometimes servers return special headers or status codes to indicate certain conditions that are important to the application workflow.

```ts
getConfigResponse(): Observable<HttpResponse<Config>> {
  return this.http.get<Config>(
    this.configUrl, { observe: 'response' });
}
```

* observe option: Tell HttpClient that you want the full response
* Now HttpClient.get() returns an Observable of typed HttpResponse rather than just the JSON data.

```ts
showConfigResponse() {
  this.configService.getConfigResponse()
    // resp is of type `HttpResponse<Config>`
    .subscribe(resp => {
      // display its headers
      const keys = resp.headers.keys();
      this.headers = keys.map(key =>
        `${key}: ${resp.headers.get(key)}`);
      // access the body directly, which is typed as `Config`.
      this.config = { ... resp.body };
    });
}
```

* HttpClient captures both kinds of errors in its HttpErrorResponse and you can inspect that response to figure out what really happened.
* Error inspection, interpretation, and resolution is something you want to do in the service, not in the component.

```ts
private handleError(error: HttpErrorResponse) {
  if (error.error instanceof ErrorEvent) {
    // A client-side or network error occurred. Handle it accordingly.
    console.error('An error occurred:', error.error.message);
  } else {
    // The backend returned an unsuccessful response code.
    // The response body may contain clues as to what went wrong,
    console.error(
      `Backend returned code ${error.status}, ` +
      `body was: ${error.error}`);
  }
  // return an observable with a user-facing error message
  return throwError(
    'Something bad happened; please try again later.');
};
```
```ts
getConfig() {
  return this.http.get<Config>(this.configUrl)
    .pipe(
      catchError(this.handleError)
    );
}

getConfig() {
  return this.http.get<Config>(this.configUrl)
    .pipe(
      retry(3), // retry a failed request up to 3 times
      catchError(this.handleError) // then handle the error
    );
}
```
