---
layout: default
title: Components
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/components/index.md
tweet: "How to use components in Angular 2"
---

_Updated November 16, 2015_

In Angular 2, Components are the main way we build and specify elements and logic on the page.

In Angular 1, we achieved this through directives, controllers, and scope. In Angular 2, all those concepts
are combined into Components.

### A simple component

Let's start with a very simple component that lists out our name:

```javascript
import {Component} from 'angular2/angular2'

@Component({
  selector: 'my-component',
  inline: '<div>Hello my name is {{name}}. <button (click)="sayMyName()">Say my name</button></div>'
})
export class MyComponent {
  constructor() {
    this.name = 'Max'
  }
  sayMyName() {
    console.log('My name is', this.name)
  }
}
```

When we use the `<my-component></my-component>` tag in our HTML, this component will be created,
our constructor called, and rendered.
