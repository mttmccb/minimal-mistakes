---
title: File > New Solution
categories:
- Long
tags:
- Visual Studio
- Yeoman
- templates
---

I've been meaning to write about 
[Template builder](https://github.com/ligershark/template-builder), I will get that post out the door, assuming it's still relevant by the time I do. What I want to think about now is different ways to create project in (or outside) Visual Studio. I posed a related question to 
[Scott Hanselman](http://www.hanselman.com) at the inaugural 
[diff.NET](https://twitter.com/diffdotnet) user group and his answer got me thinking.

My question was a little cheeky, "Why bootstrap?". I cry a little each time I have to rip out 
[bootstrap](http://getbootstrap.com) out of the web template and also when MVC views are scaffolded. While bootstrap isn't terrible, I just don't enjoy using it, I find it a little too complicated and the CSS rules too restrictive. I find myself reaching for 
!important a little too often. I'd rather use a lightweight framework like 
[pure](http://purecss.io) or 
[skeleton](http://getskeleton.com) and if it's to be a heavy weight framework then 
[foundation](http://foundation.zurb.com) would be my first choice because it's fairly modular and built with SASS in mind. In some cases I'd like to use an entirely custom framework without too much hassle.

Choice is the important thing here, but it's at the expense of a little bit of lost productivity if I don't want to use bootstrap. I'm not sure there's a easy to solution to this part so we'll leave this for another day. What this lead onto was options for templating projects.

But it's not just the front end I wanted, ideally I want a multi-project template which would include a database project, a test project, maybe a business layer or data access layer. It would likely be quite large. 
![Source: Flickr](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_5509e905e4b0a5b9540a7cb4_1426712840405__img.jpg) Source: Flickr 
##Options


Scott suggested a few options:

###Nuget Package


Setup your project template how you like and package as a NuGet Package, then when creating a new project, choose a blank project and then Install your NuGet package. This sounds promising as I could make it a little easier to version control your base project and make updates to existing projects.

###Template Builder


Create your project template using 
[Template builder](https://github.com/ligershark/template-builder), I've done this and while it was a little fiddly at first it's a very flexible option. The end result will be your template in the list of project, solutions and even items.

###Yeoman


I'd heard of 
[Yeoman](http://yeoman.io) but had never used it or really looked into it that closely but it looked very promising. It sells itself as "the web's scaffolding tool for modern webapps". From what was demoed it looks like it's possible to create a project from the command line without even opening Visual Studio. There are community built generators for all the popular frameworks and toolsets.

###Export Template


Export your project as a zip file to create your template. I believe this is the simplest option but the least flexible.

##What next?


Any approach that means I don't have to open Visual Studio is a bonus so I'll be looking at Yeoman, I think generators obviate the need for custom templates. The NuGet approach also looks interesting but it's not clear how it would work for a multi-project solution.

In reality I'm sure a combination of these methods will work.
