---
title: "Using Aurelia i18n with Typescript"
excerpt: "A tutorial on how to get setup with the Aurelia CLI and use i18next"
tags: [aurelia, i18n]
---

{% include toc title="Contents" icon="file-text" %}

It's nearly a year since I wrote about [starting with aurelia-i18n](/starting-with-aurelia-i18n/) and I did mention I would do a followup as I was looking to use [TypeScript](https://www.typescriptlang.org/) and [Webpack](https://webpack.github.io/).

I've had a few false starts with Webpack and decided to leave it until the ecosystem is fully baked, while webpack 2 has been around for a while it seems that [webpack 2.2](https://medium.com/webpack/webpack-2-2-the-final-release-76c3d43bf144) was the bigger release. A combination of poor documention and developer experience made it easy to move away from it, for now.

Typescript on the other hand has had a much smoother 2.0 release, typings are much easier to use and IDE support continues to improve. I like using typed languages and also being able to decide to which degree to use types comes in handy. Although it can be occasionally frustrating at least the issues I had were solvable.

As I'm not really concerned with webpack I prefer to use the [aurelia-cli](https://github.com/aurelia/cli) to kickstart my projects. Practically speaking I'm actually using the aurelia-cli to bootstrap a starter kit with a few things that the cli doesn't cover, which I'll write about more another time.

With that in mind I'll walkthrough how I'd get a barebone project up and running with aurelia-i18n.

## Main steps

Before I get started it'll be good to outline what steps I'm going to go walkthrough

* Create a TypeScript project using the Aurelia CLI
* Add in a basic view
* Configure aurelia-i18n
* Setup translations
* Create a language switcher
* Update existing views to use translations
* Setup testing

If you want to skip to the final result it's the [final repo](https://github.com/mttmccb/skeleton-navigation/tree/i18n).

### Step 1 - Create a TypeScript project using the Aurelia CLI

Make sure you have a recent version of node and npm.

* My versions...

```shell
npm i aurelia-cli -g
```

* Running the command

* Options

* Useful commands

#### Tweaks

* routing

### Step 2 - Add in a basic view

* Dynamic Content

* Static Content

### Step 3 - Configure aurelia-i18n

* Configuration in Main
* Configuration in aurelia.json

### Step 4 - Setup translations

* Create json files

### Step 5 - Create a language switcher

* Create language switcher component

### Step 6 - Update existing views to use translations

* Various different ways

#### Intl library

### Step 7 - Setup testing

* json files
* configure method repeat

### Possible improvements

* bundling json files
* simplify testing setup

### Conclusions