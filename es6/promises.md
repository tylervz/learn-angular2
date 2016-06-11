---
layout: default
title: Promises
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/es6/promises.md
tweet: "Promises"
---

Promises make it easier to write asynchronous code compared to using callbacks, and many libraries and Web APIs return promises for async operations, like `fetch()`:

```javascript
loadUsers() {
  fetch('/api/users').then((response) => {
    return response.json();
  }).then((data) => {
    this.users = data;
  }).catch((ex) => {
    console.error('Error fetching users', ex);
  });
}
```

We can also create our own promises using the Promise constructor, though we should rarely need to do this as it is almost always better to use a promise from an API like `fetch()` if possible:

```javascript
computeAnswerToLifeTheUniverseAndEverything() {
  return new Promise((resolve, reject) => {
    resolve(42);
  });
}
```

Promises look simple at first but are complex and powerful in practice. Take care to avoid common [anti-patterns](http://www.datchley.name/promise-patterns-anti-patterns/) with their usage.
