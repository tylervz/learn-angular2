---
layout: default
title: App Lifecycle
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/lifecycle/index.md
tweet: "Lifecycle of an Angular 2 App"
---

_Updated November 16, 2015_

Angular apps go through a multi-stage bootstrap and lifecycle process, and we can
respond to various events as our app starts, runs, and creates/destroys components.

## Bootstrap

Angular 2 apps (currently) need to be bootstrapped using the root component for the app.

In your main JS file for our app, we put this:

```javascript
{% raw %}
import {Component, bootstrap} from 'angular2/angular2';

// Annotation section
@Component({
  selector: 'my-app',
  template: '<h1>Hello {{ name }}</h1>'
})
// Component controller
class MyApp {
  constructor() {
    this.name = 'Max';
  }
}

bootstrap(MyApp)
{% endraw %}
```

This component is where you can put application-level code and configuration, and its template
is where the whole app component chain gets created.

## Component Init

When a component is created, its constructor is called. This is where we initialize state
for our component, but if we rely on properties or data from child components, we need
to wait for a digest period first.

To do this, we can wait through a `setTimeout`, or use the recommended component lifecycle event
`onInit`:

```javascript
import {Component, bootstrap, onInit} from 'angular2/angular2';

// Annotation section
@Component({
  selector: 'street-map',
  template: '<map-window></map-window><map-controls></map-controls>',
  lifecycle: [onInit]
})
// Component controller
class StreetMap {
  constructor() {
    this.name = 'Max';

    setTimeout(() => {
      // Similar to onInit below, but not recommended.
      // Could be useful in a pinch, though.
    });
  }

  setMapWindow(mapWindow) {
    this.mapWindow = mapWindow;
  }

  setMapControls(mapControls) {
    this.mapControls = mapControls;
  }

  onInit() {
    // Properties are resolved and things like
    // this.mapWindow and this.mapControls
    // had a chance to resolve from the
    // two child components <map-window> and <map-controls>
  }
}
```

## Component Lifecycle

Like `onInit`, we can track several events through the lifecycle of a component:

```javascript
import {..., onInit, onDestroy, onChange, onCheck, onAllChangesDone} from 'angular2/angular2';

// Annotation section
@Component({
  selector: 'street-map',
  template: '<map-window></map-window><map-controls></map-controls>',
  lifecycle: [onInit, onDestroy, onChange, onCheck, onAllChangesDone]
})
// Component controller
class StreetMap {
  onInit() {
    // Properties are resolved and things like
    // this.mapWindow and this.mapControls
    // had a chance to resolve from the
    // two child components <map-window> and <map-controls>
  }
  onDestroy() {
    // Speak now or forever hold your peace
  }
  onCheck() {
    // Called right after our bindings have been checked
  }
  onChange(changes) {
    // Called right after our bindings have been checked but only
    // if one of our bindings has changed.
    //
    // changes is an object of the format:
    // {
    //   'prop': PropertyUpdate
    // }
  }
  onAllChangesDone() {
    // Called right after all of our bindings have been checked
  }
}
```
