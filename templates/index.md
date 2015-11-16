---
layout: default
title: Templates
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/templates/index.md
tweet: "All about Templates in Angular 2"
---

Templates are very similar to templates in Angular 1, though there are many small syntactical changes that make it more clear what is happening.

## A simple template

Let's start with a very simple template that shows our name and our favorite thing:

```html
{% raw %}
<div>
  Hello my name is {{name}} and I like {{thing}} quite a lot.
</div>
{% endraw %}
```

## `{}`: Rendering

To render a value, we can use the standard double-curly syntax:

```html
{% raw %}
My name is {{name}}
{% endraw %}
```

Pipes, previously known as "Filters," are still in the process of being fully implemented, but will function pretty
much the same.

## `[]`: Binding properties

To resolve and bind a variable to a component, use the `[]` syntax:

```html
<video-control [player]="myPlayer"></video-control>
```

If the `<video-control>` component has declared the `player` property, it will be accessible in the instance
of the component's class.

## `()`: Handling events

To listen for an event on a component, we use the `()` stynax

```html
<my-component (click)="onClick($event)"></my-component>
```

To use event delegation, where an event on a child will bubble up to the parent, use the `^` before the event name:

```html
<my-component (^click)="onClick($event)">
  <button>I bubble up</button>
</my-component>
```
## `*`: The asterisk

`*` is a way to tell a component that there will be an embed template based on the markup. So something like this:

```html
<my-component *ng-for="object in array">
</my-component>>
```

This will create embedded template based on the markup, instead of rendering the item itself.
This is the same for `*ngIf` or any custom bindings you could have
