---
layout: default
title: ViewChild
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/viewChild/index.md
tweet: "Access child components in Angular 2"
---


_Updated April 18, 2016_

Since all components in Angular 2 have classes, you might want to call methods on these classes. This requires access to the component.

#### `@ViewChild`

To get access to a component and it's methods, we can use the `@ViewChild` annotation.

For example, our `<user-profile>` component can have a method called `sendData()`.


```javascript
{% raw %}
@Component({
  selector: 'user-profile'
})

export class UserProfile {
  constructor() {}
  sendData(){
    //send data
  }
}
{% endraw %}
```

When use the `user-profile` on our main page, we can reference the class and then assign it to a local property

```javascript
{% raw %}
import {Component, ViewChild} from 'angular2/core';
import {UserProfile} from '../user-profile';
@Component({
  template: '<user-profile (click)="update()"></user-profile>',
  directives: [UserProfile]
})
export class MasterPage {
  // we pass the Component we want to get
  // assign to a public property on our class
  // give it the type for our component
  @ViewChild(UserProfile) userProfile: UserProfile
  constructor() { }
  update(){
    this.userProfile.sendData();
  }
}
{% endraw %}
```

