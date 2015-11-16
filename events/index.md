---
layout: default
title: Angular 2 Events
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/events/index.md
tweet: "Understanding events in Angular 2"
---

Events in Angular 2 use the parentheses notation in templates, and trigger methods in a component's class. For example, assume we have this component class:

```javascript
@View(...)
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

Events that have a caret (^) before the event name perform *event delegation*. This means they fire if a child triggers that event. In general, you'll want to use event delegation to make sure you are capturing events from all children:

```html
<div id="my-profile" (^click)="clicked($event)">
  <div class="profile-image">
  </div>
  <div class="profile-text">
  </div>
</div>
```

Using event delegation, the `click` event will fire on `#my-profile` if any of the children are clicked. The event bubbles up.

## Event object

To capture the event object, pass `$event` as a parameter in the event callback from the template:

```html
<button (click)="clicked($event)"></button>
```

This is an easy way to modify the event, such as calling `preventDefault`:

```javascript
@View(...)
class MyComponent {
  clicked(event) {
    event.preventDefault();
  }
}
```
