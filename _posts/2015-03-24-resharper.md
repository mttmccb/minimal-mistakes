---
title: ReSharper is pretty sharp
tags:
- Long
- Visual Studio
- csharp
- JavaScript
- Coding
- Productivity
---

I trialled 
[ReSharper](https://www.jetbrains.com/resharper/) recently and while I'm not ready to take the jump yet (I have a few others I want to try out) it's definitely the front runner. Sadly I forgot to pause the trial while I was off work so it expired before I got a chance to write this roundup. It's a 30 day trial and I'd highly recommend you give a go.

##Alt + Enter all the things


Most coding productivity tools I've come across revolve around the keyboard and ReSharper is no different, you'll find yourself hitting Alt + Enter a lot at it brings up the menu when you highlight anything from bugs, potential improvements or refactoring. There are other shortcuts, some of which replace existing Visual Studio shortcuts, however it's handled very well when you first use the a resharper shortcut, you can opt to use ReSharper, choose another one or continue to use the default. In most case I just went all in and used the resharper shortcuts as I don't use all that many anyway.

##Refactoring made easy


ReSharper does a great job of detecting optimisations and redundancies. There were many time I inverted If statements or combined declarations which all resulted in more succinct and easier to read code.

To test it properly I tried some refactoring that were pretty painful in Visual Studio and renaming and moving code between namespaces was relatively painless. I'm pretty sure it would have taken hours rather than minutes to do the 
hard way.

##Inspection gadget
 
![](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_5511c3dde4b07319c3faa004_1427227615176__img.png) 
As well as detecting optimisations, it's so handy to have solution errors being monitored constantly, it's so easy to make a mistake and break something and now it's so much easier to get direct to the problem areas. 
Continuous Code Quality Analysis is the term they use and if you like using a common coding standard such as CamelCase then inspections will help you enforce it without too much trouble. For the most part you can run a macro to apply them solution-wide, although I'd prefer to do it on code I'm working on at the time so I can see if there's anything I'd rather not use.

##Unified TODOs


It may seem pretty minor but having all my TODOs in one place is very handy. For some stupid reason Visual Studio doesn't pick TODOs in JavaScript and I've been doing a lot of tha lately. While I don't use TODOs in code exclusively they're very handy to point myself direct to where the work needs doing.

##Tweaks


If you don't like any of the ways resharper works, it's very flexible and I adjusted the analysis settings and disabled settings on an individual file and project basis. I also used it to ignore some external files I wasn't responsible for.

##Is it worth it?


Yes, in terms of code quality. I didn't notice any degradation of performance either, if anything the error checking is better than the built-in one so it's much faster.

It's definitely the front runner and I'd find it hard to go back not using a tool like this. Next up is 
[Telerik's JustCode](http://www.telerik.com/products/justcode.aspx).
