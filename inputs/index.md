---
layout: default
title: Inputs
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/inputs/index.md
tweet: "Learn input properties in Angular 2"
---


_Updated April 14, 2016_

Components are the core of an Angular 2 app but most developers need to know how to pass data into components to dynamically configure them.

#### `@Input`

To define an input for a component, we use the `@Input` decorator.

For example, our `<user-profile>` component needs a `user` argument to render information about that user:

```html
{% raw %}
<user-profile [user]="currentUser"></user-profile>
{% endraw %}
```

So, we add an `@Input` binding to `user`:

```javascript
{% raw %}
import {Component, Input} from 'angular2/core';

@Component({
  selector: 'user-profile',
  template: '<div>{{user.name}}</div>'
})
export class UserProfile {
  @Input() user;
  constructor() {}
}
{% endraw %}
```

