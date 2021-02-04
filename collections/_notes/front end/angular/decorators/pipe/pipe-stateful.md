---
layout: post
title: Stateful Pipes
permalink: /:collection/angular/pipe
---

| Pure Functions | Impure Functions |
|---|---|
| Doesn’t have a state.  | Have an internal state. |
| same input parameters produce same output.  |
| can be safely shared with many instances.   |
| pure pipe is only called when Angular detects a change in the value or the parameters passed to a pipe. | impure pipe is called for every change detection cycle no matter whether the value or parameters changes. |

```ts
/** Pure Functions **/
const addPure = (v1, v2) => { return v1 + v2; };
addPure(1, 1); // 2
addPure(1, 1); // 2
addPure(1, 1); // 2
```

```ts
/** Impure Functions **/
const addImpure = (() => {
    let state = 0;
    return (v) => { return state += v; }
})();

addImpure(1); // 1
addImpure(1); // 2
addImpure(1); // 3
```
