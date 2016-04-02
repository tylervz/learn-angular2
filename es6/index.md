---
layout: default
title: ES6/TypeScript/AtScript/Babel...wat?
edit_link: https://github.com/driftyco/learn-angular2/edit/gh-pages/es6/index.md
tweet: "ES6/TypeScript - What is all this?"
---

One of the most difficult things for developers new to modern JavaScript
is how to actually write modern JavaScript.

There's ES5, ES6, then ES7, TypeScript, AtScript, Dart, Babel...the list goes on.

JavaScript is largely a standards-driven language. That means a [committee agrees](http://www.infoq.com/news/2015/06/ecmascript-2015-es6) on 
what "JavaScript" is, at least the lowest common denominator of it, and browser vendors
work to implement those features. Today (but not for long), ES5 is that version of JS that is
most widely supported.

However, committee-driven design is notoriously slow, so everyone from independent developers
to browser vendors are eager to use and implement new JS features faster than the standards
organization can approve them.

JavaScript as browsers understand it is a bit like the "assembly of the web," meaning that it
can correctly run code that was implemented in a higher level language and "compiled" down
to JS the browser understands.

That is exactly what CoffeeScript was, which was one of the first very successful higher-level JS languages. A developer
would write CoffeeScript, and the compiler tool would generate plain JavaScript underneath.

This is what we see today with ES6 and everything in between. Browsers don't yet implement
natively a lot of ES6+ features, and developers want to innovate on what JavaScript is. This means
they've gone to building these higher-level JS languages like AtScript, TypeScript, and tools like
Babel that implement futuristic JavaScript features and compile down to ES5.

Dart is an experimental language created several years ago by Google. We do not recommend using Dart as new JS features supersede it.

AtScript was an experimental language created by Google to extend JS and Typescript with new
features such as annotations and type introspection. It is now defunct.

Typescript is Microsoft's extension of JS that comes with powerful type checking abilities and
object oriented features. Both Angular 2 and Ionic 2 use TypeScript.

ES6 is the next version of JavaScript that was just [recently approved](http://www.infoq.com/news/2015/06/ecmascript-2015-es6) that comes with a ton of new ways to write JS. ES7 is a future standard of JS that some are already implementing
in these higher level languages.

### Conclusion

If you'd like to develop with "plain" ES6 and ES7, you can use [Babel](https://babeljs.io/), the "compiler for writing next generation JavaScript." If you'd like to use Ionic and Angular, we recommend TypeScript which will provide similar features as babel, with extra type checking if you choose to use it.

If you're interested in type checking and new OO features, or want to contribute to Angular 2, check out [TypeScript](http://www.typescriptlang.org/).

