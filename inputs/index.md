---
layout: default
title: Inputs
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/inputs/index.md
tweet: "Learn input properties in Angular 2"
---


_Updated April 14, 2016_

Components are the core of an Angular 2 app. With this, one question developers might have is how do I pass data down into my components.

In Angular 1 we did this with a directive's scope. Take the follow directive:

```javascript
{% raw %}
.controller("MainCtrl", function($scope){
    $scope.name ="Ionitron"
})

.directive('personInfo', function(){
    return{
      restrict: "E",
      scope: {
        // make the binding dynamic
        person: '='
      },
      template: '<div>{{person}}</div>'
    }
})
{% endraw %}
```

We would use this in our template like so:

```html
<person-info person="name"></person-info>
```

Now the scope in our directive experts there to be a `person` property, and this will be a dynamic value from our controller.

### `@Input`

This has been update to a simpler syntax with Angular 2. Instead of using `scope`, we can define an `@Input` for our component.

In this case, we want to define a `@Input` that will be called `person`

```javascript
{% raw %}
import {Component, Input} from 'angular2/core';

@Component({
  selector: 'person-info',
  template: '<div>{{person}}</div>'
})
export class PersonInfo {
  @Input() person;
  constructor() {}
}
{% endraw %}
```

Then when we want to use our component, we can use the following syntax.

```html
<person-info [person]="name"></person-info>
```

The `[person]` is a dynamic binding. So the value for `name` will come from our class.

```javascript
export class HomePage {
  constructor() {
    this.name = "Ionitron"
  }
}
```

