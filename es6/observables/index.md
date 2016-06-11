---
layout: default
title: Observables
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/es6/observables/index.md
tweet: "Observables"
---

Observables are event streams and a cornerstone of [Reactive Programming](https://en.wikipedia.org/wiki/Reactive_programming). While not yet an official part of ECMAScript, they are becoming ubiquitous in modern JavaScript and are in Stage 1 of the TC39 standardization process.

Unlike Promises which only fire once, Observables stream data and can be processed through powerful sequence operations.

```javascript
this.http.get('/api/cats.json')
  .map(res => res.json() || {})
  .filter(cat => cat.color == 'orange');
```
