---
layout: post
title: Decorator - @Pipe
permalink: /:collection/angular/pipe
---

* templates use pipes to improve the user experience by transforming values for display. 
* Use pipes to display, for example, dates and currency values in a way appropriate to the user's locale. 
* `@Pipe` decorator defines a function that transforms input values to output values for display in a view.
* Angular defines various predefined  pipes, such as the date pipe and currency pipe. You can also define new pipes.
* You can chain pipes, sending the output of one pipe function to be transformed by another pipe function.
* A pipe can also take arguments that control how it performs its transformation. For example, you can pass the desired format to the date pipe:

```ts
// Pipe definition
import { Pipe, PipeTransform } from '@angular/core';  
@Pipe({
name: ‘Multiplier’, 
pure: false/true     // (default is `true`)
}) 
export class MultiplierPipe implements PipeTransform { 
   transform(value: number, multiply: string): number { 
      let mul = parseFloat(multiply); 
      return mul * value 
   } 
} 
```

```ts
// Add to NgModule declarations
@NgModule ({…
   declarations: [AppComponent, MultiplierPipe],
```

```html
<!-- Default format: output 'Jun 15, 2015'--> 
<p>Today is { {today | date} }</p> 
<!-- fullDate format: output 'Monday, June 15, 2015'--> 
<p>The date is { {today | date:'fullDate'} }</p> 
<!-- shortTime format: output '9:43 AM'--> 
<p>The time is { {today | date:'shortTime'} }</p>
<!-- Using Custom Pipe -->
<p>Multiplier: { {2 | Multiplier: 10} }</p> // : for more params
```
