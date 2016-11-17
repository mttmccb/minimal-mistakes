---
title: "I'm in koherent"
excerpt: "Part 1 of a series of posts, this one tries to describe some of the factors in choosing Aurelia"
tags: [aurelia]
header:
  image: /images/desert-cropped.jpg
---

It's been a month since I started working as a Web Application Developer for PropTech startup [koherent](https://koherent.io). It has been a positive start with some unexpected challenges. I joined the company because I was excited to build a web app from scratch. In a short time I've laid some great foundations to get us towards that. 

The plan is to build a responsive single page app mainly for desktop users but also usable on other devices. Before I could dive into coding I had to make some difficult decisions including

* Which Javascript SPA framework (if any)
* Which language to use, e.g. ES2015, Typescript
* Which CSS framework (if any)
* How to build and deploy the app
* How to build a maintainable framework
* What testing to put in place
* Supporting Internationalisation (i18n) and Localisation (l10n) 
* Secure

This will hopefully be the first of a series of posts going into those decisions in more detail.

## Which Javascript SPA Framework: Aurelia
If you've been following this blog it shouldn't surprise you that I chose [Aurelia](https://aurelia.io), I even gave a [short talk](http://www.meetup.com/unified-diff/events/232440137/) about it. I did briefly consider using no framework as they can be a little too opinionated but I didn't fancy reinventing the wheel. There are a lot of good reasons to choose Aurelia over the other options and I'll go into why it was a good fit for this project.

Since it was released in early 2015 there have been very few breaking changes, as it was an evolution of the SPA framework [Durandal](http://durandaljs.com/) it has borrowed a lot of the best parts from that. Such as the routing and component lifecycle. To bring it up to date it was build on the latest web standards such as ES2015, Shadow DOM and of course Web Components.

The framework favours convention over configuration, which can mean things are a little like magic. But I find clear conventions a plus, there is very little boilerplate code and by following some simple conventions your view models and components are very clean. What means in reality is it's easy to understand and maintain even for developers not familia with Aurelia. As the MVVM pattern is well understood this also contributes to giving Aurelia a shallow learning curve. 

Poor documentation was an early criticism however this has improved considerably and a lot of support is available via an active community on Gitter. It's so good it got Rob Eisenberg a new job as Sr. Program Manager on the team that builds [docs.microsoft.com](https://docs.microsoft.com).

The bad sides of Aurelia are shared by most SPA frameworks, setup and tooling. There's no denying it's complicated and it's likely at some point you're going to lose a few days due to inexplicable configuration issues. There are 2 main ways to get started using one of the setups in the [Skeleton Navigation](https://github.com/aurelia/skeleton-navigation) or using the [Aurelia CLI](https://github.com/aurelia/cli). The main factor in choosing between them is if you want to use Webpack or not, the CLI doesn't currently support it.

If you're into the Microsoft stack then you might be interested in [JavascriptServices](https://github.com/aspnet/JavaScriptServices). It's a project that will help get you up and running with .NET Core and Aurelia (or a number of other SPA frameworks), it also uses Webpack. I'll go into Webpack in another post but all you need to know right now it's that it's a desirable tool in a SPA.

If I were to narrow it down to 3 reasons (I like 3s)

* **Developer friendly** - this is a catch all for being easy to understand, maintain and code with, all of which is important for a small team.
* **Modular** - I haven't mentioned this until now but Aurelia is essentially a combination of discrete modules which you can pick and choose. This give you flexible to only include what you use.
* **Well supported** - Either by getting help in the Gitter chatroom, picking up an eBook, reading through the docs, blog posts, stack overflow, pluralsight and training and consultancy provided by the Aurelia team.

## The "competition"
Of course Aurelia isn't the only SPA framework around, there are quite a few. It would be irresponsible not to at least consider the alternatives. I've read or heard about most of these frameworks, used a few and even heard from a few of their creators. I'm not going to go to give a detailed comparison but I'll give you a few of a pros and cons of the main players. There isn't much in it when it comes to the performance of the various frameworks, but depending on your use case this might be a factor. I think the biggest factor should be speed of development and maintainability of the final result. Let's get into the other frameworks.

[MeteorJS](https://meteorjs.com) looked promising but it's too closely tied to MongoDB, which is fine if you want to use MongoDB. It's one of the few frameworks that began with Javascript on the client and server but it still requires jQuery and Underscore. It's probably good for a prototype but I'd have concerns about using it longer term.

[Angular 1](https://angular.io) and [Backbone.js](http://backbonejs.org/), are both widely used and very stable but they don't take advantage of modern browsers. I'm not a huge fan of the verbosity of Angular and the amount of code you need to write to get something up and running. Some of the patterns in both are not the easiest the handle either. If I were building an app 3 years ago these would probably be top of the list.

I like the binding syntax of [Knockout](https://knockoutjs.com) but I did run into problems with larger apps. Some of these might have been solved by using [Durandal](https://durandaljs.com) but I didn't have the right project to use that on. Knockout is still under active development but I'm not convinced the community will continue to support it. 

Rob Eisenberg was part of the [Angular 2](https://angular.io/) team at one point but left as he disagreed with the direction they're going, I can see why. I struggle to understand why it's such a popular framework, the configuration is over the top, the binding syntax is just horrible and they can't seem to write a router (React also has this problem). There is so many proprietary warning signs in there and it seems to be very unstable, Angular 2 was just never something I'd end up choosing. I'm sure if I had to use it I'd get used to it but the steep learning curve (note the number of courses and books about it...) is a little off putting. Do you really think Google are committed to it?

[React](https://facebook.github.io/react/) is a tricky one, it's technically just a view engine, not a complete framework, you'd typically add something like [Flux](https://facebook.github.io/flux/docs/overview.html) or [Redux](http://redux.js.org/docs/basics/UsageWithReact.html). It introduces a number of new features such as one-way data flow and even it's own language, JSX, it's fair to say it encourages a more functional programming style. It has got *a lot* of hype for it's testability and development speed. But this seems to come at cost of merging your javascript, HTML and CSS into one file. I've yet to see an example that isn't a complete mess and because it's so different you're locked into it. I don't see Facebook abandoning it as easily as Google would but I trust them less, particularly as they felt the need to add a patent clause into their licence. As there are number of new concepts and no real track record using them you're going to be in for a rough ride.

[Vue.js](https://vuejs.org/) is another one with a lot of hype but I haven't really used it. I've heard the creator of the framework on a few podcasts and I'm not convinced he has a clear idea. The [migration guide](https://vuejs.org/v2/guide/migration.html) from v1 to v2 make me thinking there is a lot of new shiny feature chasing. The binding syntax is a little Angular-like with symbols which isn't really intuitive to me. It's mainly the instability of it that puts me off.

[EmberJS](http://emberjs.com/) was probably the most promising, it has stability, clear conventions and good support. However performance and size weren't great and it's a little too rigid in doing things in the "Ember way". The templating side of ember looks pretty straightforward but the examples I've seen appear to require a bit too much code for something simple.

Despite my criticism of the other frameworks I think it's great there are so many around as they are pushing each other forward. [Javascript Jabber](https://devchat.tv/js-jabber/237-jsj-clls-ember-angular-and-react-with-tracy-lee) cover how the different CLIs are being merged and shared around the main frameworks and the Aurelia CLI somewhat based on the Angular one. It's unfortunate that it has got so complex that a CLI is needed to get most project up and running but they really do help with a lot of plumbing.

## The future of Aurelia
Aurelia just hit 1.0 earlier this year and the latest announcement about [Aurelia UX](http://blog.aurelia.io/2016/11/04/introducing-aurelia-ux/) shows the team aren't finished developing Aurelia, it wasn't a quick decision and it's a change from the original plan. What it could mean is that developing cross-platform mobile apps with a common code base is easier. As it's pre-alpha it's difficult to recommended it but it looks promising.

Right now you could wrap an Aurelia app in [Electron](http://electron.atom.io/) to give you a cross-platform desktop app.

Neither of these are high priority for this particular project but it's good to know, it's also a promise I've heard of React with React Native but I've not heard that it's actually worked out that well.

There continue to be new plugins and libraries and existing ones are being maintained so I'm not too worried about the future of Aurelia.

## Right decision?
It would be easy to say I have chosen the framework I know best and justified my reasons for choosing it. Thankfully I can take a step back, I mean I enjoyed watching *Lost* but there is no justifying that ending.

It is a little worrying that it doesn't get the same level of buzz as some of the bigger frameworks. However whichever framework you choose, it will have a limited shelf life. As Aurelia keeps the framework specific code to a minimum it wil make it easier to port to another framework in the future. You'd have a difficult time doing the same with React and Angular 2.

On balance I think it's the right choice, right now.