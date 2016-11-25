---
title: "Choosing a language for your SPA"
excerpt: "Part 2 of a series of posts, where I compare different flavours of Javascript, Typescript and choose one"
tags: [aurelia]
header:
  image: /images/bluesky2-cropped.jpg
---

{% include base_path %}

In the [previous post](https://mttmccb.github.io/im-in-koherent/) I chose to use the [Aurelia](https://aurelia.io) framework. Now to pick the language to use with the framework. If you look at code samples in the docs you're given 3 options

* ES Next
* Typescript
* ES 2015

You're probably wondering where Javascript is, that would be the 2 ES options, or Ecmascript to confuse the beginners. I'm sure there is a good reason to refer to by the name of the standard but I don't know what is it.

There have been plenty of explanations of what these all mean, such as [Understanding ES5, ES2015 and Typescript](Understanding ES5, ES2015 and TypeScript) by John Papa which gives a bit more background and detail.

It's worth noting these decisions aren't unique to Aurelia, all the main frameworks have made similar choices as communities and clearly favour one over the other.

## ES 2015 (or ES6)
Unless you enjoy pain and suffering you're not going to use the earlier version of Javascript (ES5). While it's widely supported by browsers it isn't particularly productive to write due the gnarly syntax. Unfortunately that means you're going to need a build step to transpile your ES2015 code to ES5, especially if you want to support older browsers and some mobile browsers. You can view the [detailed compatibility table](https://kangax.github.io/compat-table/es6/) if you're not sure.

In the case of ES2015 this usually means you'll use [Babel](https://babeljs.io/) to handling transpilation, although [Traceur](https://github.com/google/traceur-compiler) was also a good choice Babel has become the de facto standard.

### WTF is transpilation and why do I need to do it?
It's a bit like compilation, compilers will translate your high level code into lower level code, for example, C compiles to assembler. Transpilation on the other hand translates your high level code into another high level code in another language, for example, C# to Visual Basic. In this case it's from ES 2015 to ES5, which is what most current browsers understand.

The reason you'd want to do this is because you want to write more maintainable code using cleaner syntax and language features available in the newer standard of the language. While transpiling is not ideal it's relatively well understood and the benefits of doing it vastly outweight the downsides.

Even when browsers catch up I can't see transpilation going away as it's the easy way to access new features. Some of these might be just syntatic sugar which are no brainers but some may require polyfilling to implement, which may impact your decision. Transpilers like Babel allow you to be select the features you want to support and there is a wealth of configuration to suit your needs.

## ES Next
This brings us to ES Next, which is just a placeholder for what ever the next version of Javascript will be, right now it's ES 2017, as ES 2016 was just standardized. Javascript is now on a yearly release cycle after it didn't really see changes for about 5 or 6 years. That doesn't mean you should expect lots of new features to appear, just look at the index of the [Exploring 2016 and ES2017](http://exploringjs.com/es2016-es2017/) book and you can see there were only a few features in ES2016, ES2017 is a bit more substantial.

Whatever you are using you'll probably want to understand what stage the features you're using are in. It's possible they haven't been implemented in browsers (or even if they have) be careful when relying on them. Decorators are a good example of a feature that is widely used in SPAs but is usually still considered experimental, if it would pulled now it would cause a lot of disruption.

## Where does Typescript fit in?
Typescript is a typed Javascript-like language that transpiles to Javascript. It was developed by Microsoft (Anders Hejlsberg) but has become more widely adopted, for example Angular 2.0 switch to Typescript. It’s similar to ES2015 but has features that aren’t in any version of Javascript. It add optional type annotations, visibility and decorators. The compiler uses these for checks but they removed from the compiled code.

By annotating variables, class and functions it makes it possible to spot errors at design time that would normally not be picked up at runtime. If a code base is large then it can make it easier to analyse and reliably refactor code. This is especially important in a long term project. This does fall down a little with Aurelia when you're renaming a property as it doesn't update your HTML views.

Typescript isn't the only way to implement type checking, you could use [Flow](https://flowtype.org/). The advantage Flow has is that you are still writing Javascript, technically Typescript is another language and even uses a different file extension.

I think a type system is essential in longer term and particularly team projects. If you want a more indepth look into the options, including Elm, then Oliver Ziergermann has a [great series of presentations](https://djcordhose.github.io/flow-vs-typescript/elm-flow-typescript.html).

### The pain of Typings
It's not all easy with Typescript and it's only recently they've settled on a good way to handling the types for 3rd party libraries. A lot of libraries are now listed on [DefinitelyTyped](http://definitelytyped.org/) and there is nothing stopping you write typings for a library if they don't already exist.

Another area where it can get tricky is the module system, I can't say I fully understand but I did find the `AllowSyntheticImports` option useful when libraries weren't quite in the right format. Nothing was broken but it did mean it was producing error messages for no good reason.

The main code editor I use [VS Code](https://code.visualstudio.com/) has pretty good support for Typescript but make sure you understand the impact of changing the options in the `.tsconfig` file. While it might mean things compile you might just be hiding problems instead of dealing with them. `NoImplicitAny` is another useful flag which is a good way to spotting any missing or mistmatched typings but can be quite painful on large codebases because it will likely explode with a lot of errors.

## TSlint
I strongly believe in coding standards but I don't think we should ever have to remember every little intracy of them. For that we can using linting tools like [tslint](https://palantir.github.io/tslint/), which help to keep your code consistent with the standards you set. It's probably a good idea to use one of the existing standards such as `tslint:recommended` and adapt it to fit your needs, there are a lot of rules and expect to tweak your rules over time.

## Final decision
Going with Typescript for this project was a pretty easy choice because of the potential for change and growth of the codebase. It's now in version 2 and it's pretty mature and has good IDE support.

I would like to try out Flow in the future but it doesn't seem like a good fit here.