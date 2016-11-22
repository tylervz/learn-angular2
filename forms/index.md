---
layout: default
title: Forms
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/forms/index.md
tweet: "Build great forms in Angular 2"
---

Forms are the cornerstone of any real app. In Angular 2, forms have changed quite a bit from their v1 counterpart.

Where we used to use `ngModel` and map to our internal data model, in Angular 2 we more explicitly build forms and form controls.

While it feels like more code to write, in practice it's easier to reason about than with v1, easier to unit test, and we no longer have to deal with frustrating ngModel and scope data problems.

## Simple Form

Let's start with a simple login form in HTML with Angular 2.

App Module:
```javascript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
// We need to import the ReactiveFormsModule and import it
import { ReactiveFormsModule } from '@angular/forms';
import { HttpModule } from '@angular/http';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    ReactiveFormsModule,
    HttpModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Template:
```html
<form [ngFormModel]="loginForm" (ngSubmit)="doLogin($event)">
    <input formControlName="email" type="email" placeholder="Your email">
    <input formContControl="password" type="password" placeholder="Your password">
  <button type="submit">Log in</button>
</form>
```

Component Class:
```javascript
import { Component } from '@angular/core';
import { FormBuilder, Validators } from '@angular/forms';

@Component({
  selector: 'login-page',
  templateUrl: 'login-page.html'
})
export class LoginPage {
  public loginForm = this.fb.group({
    email: ["", Validators.required],
    password: ["", Validators.required]
  });
  constructor(public fb: FormBuilder) {}
  doLogin(event) {
    console.log(event);
    console.log(this.loginForm.value);
  }
}

```

When we run this, we are shown a simple login form with email and password:

![ex](ex1.png)

## FormBuilder

The FormBuilder from the example above makes it easy for us to specify form controls and the various
validators we might want to apply to certain controls.

In the example above, we are creating two inputs, an `email` and `password` field:

```javascript
public loginForm = this.fb.group({
  email: ['', Validators.required],
  password: ['', Validators.required],
});
```

## ControlGroup

The `FormBuilder` creates instances of `FormGroup`, which we refer to as a `form`.

Instead of using the `FormBuilder`, we could also construct the `FormGroup` manually:

```javascript
import { FormGroup, FormControl } from '@angular/forms';

...

public loginForm = new FormGroup({
  email: new FormControl("email", Validators.required),
  password: new FormControl("password", Validators.required)
});
```
In practice though, the `FormBuilder` is what we will use to quickly create forms.

## Form Directives

You'll notice the lack of `ngModel` anywhere in our form. Instead, we have the `formControlName` directies that map certain inputs to our control objects:

```html
  <input formControlName="email" type="email" placeholder="Your email">
```

This "binds" the email input to the instance of our `email` control.

## Custom validators

We can build custom form validators as a simple function:

```javascript
function containsMagicWord(c: FormControl) {
  if(c.value.indexOf('magic') >= 0) {
    console.log('not valid')
    return {
      noMagic: true
    }
  }

  // Null means valid, believe it or not
  console.log('valid')
  return null
}

this.loginForm = fb.group({
  email: ['', containsMagicWord]
  password: ['', Validators.required],
});
```

## Handling form values

We can easily get the simple Typescript object value of our form, or the value of an individual control:

```javascript
doLogin(event) {
  // Show the value of the form
  let formData = this.loginForm.value;
  // { email: 'blah@blah.net', password: 'imnottelling1' }

  // Or, grab the value of one control:
  let email = this.loginForm.controls.email.value

}
```
