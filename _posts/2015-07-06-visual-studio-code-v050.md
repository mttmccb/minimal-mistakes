---
title: Visual Studio Code v0.5.0
categories:
- Long
tags:
- Visual Studio
---

I'm going to keep this up I hope... and I was panicking that I'd missed a version of Visual Studio Code (VSC) as I could swear the last one was 
[v0.3.0](http://mttmccb.net/blog/2015/visual-studio-code-v030), which is it was. Read the 
[release notes](https://code.visualstudio.com/Updates/) yourself if you're interested or the 
[blog summary](http://blogs.msdn.com/b/vscode/archive/2015/07/06/visual-studio-code-july-update-0-5-0.aspx). 
Just to recap, I'm using VSC it for an 
[aurelia](http://aurelia.io) based project for an 
[app.net](http://app.net) web client called 
[Dark Social](http://darksocial.azurewebsites.net). I'm using the TypeScript yet but aurelia does use a lot of ES6 and 7 features. 
Let's run through the updates... 
#ES6 support and jsconfig.json
 
Finally, I hope make things a little easier while I transition to TypeScript. It also explains my entire module being covered in red squigglies. I need a jsconfig.json file apparently. So far I've been pretty much ignoring all the errors and warnings as most of them weren't problems. This is new and may also mean nothing as I can't see any duplicates. 
![](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_559ad97fe4b003deab7c8b59_1436211586705__img.png) 
##Hiding derived resources
 
Definitely one for TypeScript and one I'll need to review later. Although it could apply to LESS too I keep all my derived resources in my 
dist folder anyway. 
##Git Enhancements
 
If you call multi-line support an enhancement rather than a basic feature then it's an improvement. Too many time I've pressed 
Enter and commited rather than dropping a new line so this will be very handy. Just need to remember 
Alt+Enter to actually do the commit. 
##Debugging...
 
I've barely touch this due to the weird setup of aurelia, I just got unit testing working so maybe this is next on the list to sort out as I'm sure it would make my life easier. 
##That's it...
 
There may be more for you but a few of those changes will make some of my niggles go away.
