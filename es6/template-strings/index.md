---
layout: default
title: ES6 Template Strings
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/es6/template-strings/index.md
tweet: "Magical new ES6 Template Strings"
---

ES6 adds the ability to write long inline strings without having to use concatenation or other odd tricks. All we need to do is use backticks at the start and end of the string:

```html
let template = `
  <div>
    <h2>Rufferford's Travels</h2>
    <p>
      A most gripping tale of one dog's quest
      for more flavors.
    </p>
  </div>
`;
```

You can also do string interpolation using ${expression} placeholders:

```html
let x = 5;
let y = 10;
let template = `
  <div>The sum is <span>${ x + y }</span></div>
`;
```
