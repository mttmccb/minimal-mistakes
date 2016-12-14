---
title: 'Typescript or ES6: Slightly Loaded Question'
tags:
- es6
- JavaScript
- TypeScript
---

In my previous post I mentioned I'd been playing around with TypeScript, however the same goes for ES6 and I've probably put slightly more hours into that. This won't be a great argument for or against but I'll try to summarize some of the main points, may there will be a conclusion at the end. 

* Google is using it for [Angular 2.0](http://techcrunch.com/2015/03/05/microsoft-and-google-collaborate-on-typescript-hell-has-not-frozen-over-yet/). 
* This was first reported in March 2015 and given these things changed like the wind I didn't pay much attention to it. However it seems like they were serious afterall.
* TypeScript is a superset of ES6.
* ES6 has no types, TypeScript does.
* Both currently compile to current standard JavaScript however I suppose ES6 will 
eventually be able to drop the build step.
* Considerable less testing is required for TypeScript as a lot of error are picked up if the wrong type is used.
* Existing projects can use [Typings](https://github.com/borisyankov/DefinitelyTyped).
* You can write more robust and efficient code in both languages.
* Debugging I'm less sure of but from what I've seen you can debug the ES6/TypeScript rather than the JavaScript it transpiles.
* For small projects vs large projects 
* it might be that JavaScript is ok for small snippets.
* Existing vs New Projects 
* Converting an existing project to TypeScript might be painful but starting on a new one would be ok.

It's probably worth mentioning it's possible to continue coding with current JavaScript and adopt new features as they become widely available. 

I think I'm heading toward transpiled JavaScript languages and TypeScript seems like the best choice but learning all the features of ES6 is essential as they will probably form part of TypeScript and definitely part of JavaScript. However if it's the future I should probably 
[study the roadmap](https://github.com/Microsoft/TypeScript/wiki/Roadmap).