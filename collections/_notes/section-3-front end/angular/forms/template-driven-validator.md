---
layout: post
title: Validator functions
permalink: /:collection/angular/forms/template-driven/validator
---

*	**Sync validators**: functions that take a control instance and immediately return either a set of validation errors or null. You can pass these in as the second argument when you instantiate a FormControl.
*	**Async validators**: functions that take a control instance and return a Promise or Observable that later emits a set of validation errors or null. You can pass these in as the third argument when you instantiate a FormControl.
*	styles.css ==> @import url('https://unpkg.com/bootstrap@3.3.7/dist/css/bootstrap.min.css');
*	**Why check dirty and touched?** Don’t want want to display errors before user edit the form.

| Properties |                                                                                       |
| ---------- | ------------------------------------------------------------------------------------- |
| valid      | This property returns true if the element’s contents are valid and false otherwise.   |
| invalid    | This property returns true if the element’s contents are invalid and false otherwise. |
| pristine   | This property returns true if the element’s contents have not been changed.           |
| dirty      | This property returns true if the element’s contents have been changed.               |
| untouched  | This property returns true if the user has not visited the element.                   |
| touched    | This property returns true if the user has visited the element.                       |
