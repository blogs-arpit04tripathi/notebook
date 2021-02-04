---
layout: post
title: Data Driven Form (Reactive Form)
permalink: /:collection/angular/forms/data-driven
---

```html
<form [formGroup]="profileForm" (ngSubmit)="onSubmit()>
   <label>First Name:<input type="text" formControlName="firstName"></label>
   <label>Last Name:<input type="text" formControlName="lastName"></label>
   <div formGroupName="address">
      <h3>Address</h3>
      <label>Street:<input type="text" formControlName="street"></label>
      <label>City:<input type="text" formControlName="city"></label>  
      <label>State:<input type="text" formControlName="state"></label>
      <label>Zip Code:<input type="text" formControlName="zip"></label>
   </div>
   <button type="submit" [disabled]="!profileForm.valid">Submit</button>
</form>
```

```ts
export class ProfileEditorComponent {
  profileForm = new FormGroup({
    firstName: new FormControl(''),
    lastName: new FormControl(''),
    address: new FormGroup({
      street: new FormControl(''),
      city: new FormControl(''),
      state: new FormControl(''),
      zip: new FormControl('')
    })
  });
}
```

```html
<input id="name" class="form-control"
      formControlName="name" required >
<div *ngIf="name.invalid && (name.dirty || name.touched)"
    class="alert alert-danger">
  <div *ngIf="name.errors.required">
    Name is required.
  </div>
  <div *ngIf="name.errors.minlength">
    Name must be at least 4 characters long.
  </div>
  <div *ngIf="name.errors.forbiddenName">
    Name cannot be Bob.
  </div>
</div>
```
```ts
ngOnInit(): void {
  this.heroForm = new FormGroup({
    'name': new FormControl(this.hero.name, [
      Validators.required,
      Validators.minLength(4),
      forbiddenNameValidator(/bob/i)
    ]),
    'alterEgo': new FormControl(this.hero.alterEgo),
    'power': new FormControl(this.hero.power, Validators.required)
  });
}
get name() { return this.heroForm.get('name'); }
get power() { return this.heroForm.get('power'); }
/** A hero's name can't match the given regular expression */
export function forbiddenNameValidator(nameRe: RegExp): ValidatorFn {
  return (control: AbstractControl): {[key: string]: any} | null => {
    const forbidden = nameRe.test(control.value);
    return forbidden ? {'forbiddenName': {value: control.value}} : null;
  };
}
```
