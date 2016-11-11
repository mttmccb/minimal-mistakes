---
title: "CSS naming and setup roundup"
excerpt: ""
tags: [CSS, BEM, ITCSS, OOCSS, SMACSS]
header:
  image: 
  caption: ""
---

I'm going to take on a new project next month and I want to start on the right foot, so I've been looking closely at the current state of CSS. In term of setting a maintainable and scalable system for handling a component based application. I think this is a little different to a standard website but the lines are blurring. Just take a look at [Shaun Bent](https://medium.com/@shaunbent/css-at-bbc-sport-part-1-bab546184e66#.195ve67b1) described BBC Sport's CSS architecture.

Clearly they're a huge organisation with a massive amount of traffic so this might not fit the needs of the project. So what am I aiming for? Well the first thing is that it's going to be a SPA, probably [aurelia](http://aurelia.io) so it would be great to complement the convention it uses.

## Must have's from a CSS architecture

- Low specificity
  - Overrides quickly escalate, particularly when you start adding responsive style so starting low is best
- Theming
  - Easy to add fonts, colours and images
- i18n / l10n
  - That's internationalization and localization, this is more of a design decision but worth keeping in mind
- Consistent and maybe enforceable
  - A style that is consistent and easy to understand and read is important but having some automated tool to make sure things are straying is great.
- Extendable and predictable
  - Add new components or changing existing one should be predictable and easy

## Pre-Processor and Post-Processor
While you can get by with plain CSS it become painful to manage large projects. I had been looking at [SASS](http://sass-lang.com/) and while I've used it in the past I've never been a big fan of it, I found it to be a little bloated and slow, it's probably a lot to do with the need for Ruby. But I read with interest [Breaking up with Sass: it’s not you, it’s me](https://benfrain.com/breaking-up-with-sass-postcss/) by Ben Frain as I was looking into using [PostCSS](http://postcss.org/). On the surface it appears to be a much lighter tool, it's more like 2 slices of bread waiting for you to fill it with something, whether that's [autoprefixer](https://autoprefixer.github.io/) or [cssnext](http://cssnext.io/) (both PostCSS plugins).

I'd also recommend [Ashley Nolan's](http://ashleynolan.co.uk/blog/postcss-a-review) review of PostCSS, it's probably a little out of date now but great if you're coming from SASS. As is the very enigmatic presentation from [Audrey Sitnik](http://ai.github.io/about-postcss/en/) which covers a lot of the reasons why you should consider PostCSS.

While it's possible to use [PostCSS together with Sass, Stylus or LESS](http://webdesign.tutsplus.com/tutorials/using-postcss-together-with-sass-stylus-or-less--cms-24591) I think it add unnecessary complexity. (BTW Kezz Bracey's [PostCSS Deep Dive](http://webdesign.tutsplus.com/series/postcss-deep-dive--cms-889) is great).

[Karolina Szczur](https://www.youtube.com/watch?v=1vbBLc-fgWk)
https://www.youtube.com/watch?v=1vbBLc-fgWk

## Naming

https://css-tricks.com/developing-extensible-html-css-components/

The front runner here is [BEM](https://en.bem.info/) (Block-Element-Modifier)
http://webdesign.tutsplus.com/tutorials/using-postcss-with-bem-and-suit-methodologies--cms-24592


## Namespaces
http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/
Pantsuit CSS
ShadowDOM
Scoped

http://csswizardry.com/2015/08/bemit-taking-the-bem-naming-convention-a-step-further/

## Organising

## Into Production