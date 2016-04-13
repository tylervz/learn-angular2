---
layout: default
title: Inputs
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/outputs/index.md
tweet: "Emit your own crazy even with Outputs in Angular 2"
---


_Updated April 14, 2016_


If you want to bind to particular event, you can use the new [Event syntax](/events) in Angular 2. But what if you need your own custom event?


To create a custom event, we can use the new @Output decorator. Take the following component:

```javascript
import {Component} from 'angular2/core';

@Component({
  selector: 'person-info',
  template: '<div>Hello</div>'
})
export class PersonInfo {
  constructor() {}
}
```

Let's import `Output` and `EventEmitter` and create our new event

```javascript
import {Component, Output, EventEmitter} from 'angular2/core';
@Component({
  selector: 'person-info',
  template: '<div>Hello</div>'
})
export class PersonInfo {
  @Output() everySecond = new EventEmitter();
  constructor() {
    setInterval(() => {
      this.everySecond.emit('event');
    }, 1000;
  }
}
```

Now when we used this component elsewhere in our app, we can bind the event that `person-info` emits

```html
  <person-info (everySecond)="logEvent($event)"></person-info>
```

```javascript
export class MyClass {
  constructor(){}
  logEvent() {
    console.log('second');
  }
}
```
