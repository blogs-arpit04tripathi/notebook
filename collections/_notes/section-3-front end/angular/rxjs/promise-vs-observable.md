---
layout: post
title: Promise vs Observable
permalink: /:collection/angular/rxjs/promise-vs-observable
---

![promise-vs-observable]({{site.cdn}}/angular/promise-vs-observable.png)

| Promise                                                            | Observable                                                                   |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| handles a single event when an async operation completes or fails. | stream of zero or more events where the callback is called for each event.   |
| Has only one pipeline  | Streams data in multiple pipelines  |
| Only .then()           | Provides chaining and subscription  |
| Not Lazy               | Lazy - emits values when time progresses |
| Not cancellable   | Cancellable – heavy operations that are not needed anymore by .unsubscribe() |
| possible decisions– Reject, Resolve |
| Cannot be retried   | retry(), or replay() or retryWhen       |
|                      | operators like map, forEach, reduce, filter    |
| Push errors to child promises  | Subscribe method for centralized and predictable error handling.  |

![observalble-code]({{site.cdn}}/angular/observalble-code.png)
