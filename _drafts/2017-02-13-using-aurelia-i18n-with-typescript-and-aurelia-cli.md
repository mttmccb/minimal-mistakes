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

With that in mind I'll walkthrough how I'd get a barebone project up and running with aurelia-i18n. If you want to skip to the final result it's the [final repo](https://github.com/mttmccb/skeleton-navigation/tree/i18n).

## Setting up the project

First we want to create a TypeScript project using the Aurelia CLI. Make sure you have a recent version of node and npm. I'm using the following

```shell
node -v
v7.4.0
npm -v
4.0.5
```

If something strange goes wrong then either of these could be the reason. I recently had to upgrade to the 4.x branch of NPM to resolve an issue.

As we're going to use the Aurelia CLI we need to install it with the following command.

```shell
npm i aurelia-cli -g
```

As I've already created a repo (with a .gitignore and LICENCE file) and cloned it to my local machine I can create a new project from the repo folder like this.

```shell
au new --here
```

Then we'll choose the following options from the wizard

1. Enter - Web (Default)
1. 2 - Typescript
1. 2 - Minimum Minification, I have used Maximum but it removed spaced I didn't want it to
1. Enter - None (Default), we don't need a preprocessor for this
1. Enter - Yes (Default) to unit testing, We'll do a little that later
1. Enter - Yes (Default) to Visual Studio Code, it's a great editor for web development
1. Enter - Yes (Default) to create the project, if you got something wrong now would be the time to use restart
1. Enter - Yes (Default) to install the dependencies

Give it a couple of minutes to install everything and to check everything is working run

```shell
au run --watch
```

Open [http://localhost:9000](http://localhost:9000/) in your browser and you should see "Hello World". You can make some changes files in the `src` folder and they should be reflected in the browser.

It's a good idea to add `scripts` to your `.gitignore` at this point. You bundled files are generated to this folder but you probably don't want them in your repo.

Next we'll can run the tests using `au test --watch`.

You can modify the environment of either of these commands with `--env` for example `au run --env prod --watch`

Without too much effort we've got a working Aurelia project using Typescript with unit testing configured and we run it in dev or prod.

## Add in a basic view

* Dynamic Content
* Static Content

## Configure aurelia-i18n

* Configuration in Main
* Configuration in aurelia.json

## Setup translations

* Create json files

## Create a language switcher

* Create language switcher component

## Update existing views to use translations

* Various different ways

### Intl library

## Setup testing

* json files
* configure method repeat

## Possible improvements

* bundling json files
* simplify testing setup

## Conclusions

CLI good for quickly getting started.