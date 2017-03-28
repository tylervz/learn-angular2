---
layout: default
title: ViewChild
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/viewChild/index.md
tweet: "Access child components in Angular 2"
---

Child components in our view can be accessed from our parent component easily with `@ViewChild`.

#### `@ViewChild`

To get access to a component and its methods, we can use the `@ViewChild` decorator.

For example, our `<user-profile>` component can have a method called `sendData()`.

<h5>child.component.ts</h5>
```javascript
{% raw %}
@Component({
  selector: 'user-profile'
})

export class UserProfile {
  constructor() {}
  sendData() {
    //send data
  }
}
{% endraw %}
```

When use the `user-profile` on our parent component, we can reference the `UserProfile` component class and then assign it to a local property:
<h5>parent.component.ts</h5>
```javascript
{% raw %}
import { Component, ViewChild } from '@angular/core';
import { UserProfile } from '../user-profile';

@Component({
  template: '<user-profile (click)="update()"></user-profile>',
})
export class MasterPage {
  // ViewChild takes a class type or a reference name string.
  // Here we are using the type
  @ViewChild(UserProfile) userProfile: UserProfile

  constructor() { }

  ngAfterViewInit() {
    // After the view is initialized, this.userProfile will be available
    this.update();
  }

  update() {
    this.userProfile.sendData();
  }
}
{% endraw %}
```


We can also do the same thing with a local variable.
Instead of trying to load the particular class, we can do:
<h5>parent.component.ts</h5>
```javascript
{% raw %}
import { Component, ViewChild } from '@angular/core';
import { UserProfile } from '../user-profile';

@Component({
  template: '<user-profile #myProfile (click)="update()"></user-profile>'
})
export class MasterPage {
  @ViewChild('myProfile') userProfile: UserProfile
  constructor() { }
  update(){
    this.userProfile.sendData();
  }
}
{% endraw %}
```
