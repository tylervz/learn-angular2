---
layout: default
title: Angular 2 Events
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/events/index.md
tweet: "Understanding events in Angular 2"
---

Events in Angular 2 use the parentheses notation in templates, and trigger methods in a component's class. For example, assume we have this component class:

```javascript
@Component(...)
class MyComponent {
  clicked(event) {
  }
}
```

And this template:

```html
<button (click)="clicked()">Click</button>
```

Our `clicked()` method will be called when the button is clicked.

## Delegation

Events in angular two behave like normal DOM events. They can bubble up and propagate down. Nothing special to do here!

## Event object

To capture the event object, pass `$event` as a parameter in the event callback from the template:

```html
<button (click)="clicked($event)"></button>
```

This is an easy way to modify the event, such as calling `preventDefault`:

```javascript
@Component(...)
class MyComponent {
  clicked(event) {
    event.preventDefault();
  }
}
```
