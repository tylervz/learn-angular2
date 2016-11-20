---
layout: default
title: Components
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/components/index.md
tweet: "How to use components in Angular 2"
---

In Angular 2, "everything is a component." Components are the main way we build and specify elements and logic on the page, through both custom elements *and* attributes that add functionality to our existing components.

### A simple component

Here's a simple [Component](https://angular.io/docs/ts/latest/api/core/index/Component-decorator.html) that renders our name, and a button that triggers a method to print our name to the console:

```javascript
{% raw %}
import { Component } from '@angular/core';

@Component({
  selector: 'my-component',
  template: '<div>Hello my name is {{name}}. <button (click)="sayMyName()">Say my name</button></div>'
})
export class MyComponent {
  constructor() {
    this.name = 'Max'
  }
  sayMyName() {
    console.log('My name is', this.name)
  }
}
{% endraw %}
```

When we use the `<my-component></my-component>` tag in our HTML, this component will be created,
our constructor called, and rendered.
