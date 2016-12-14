---
title: Unit Testing MVC Controllers with Fluent MVC Testing
categories:
- Long
tags:
- csharp
- asp.net mvc
- coding
- unit testing
- controllers
---

This post is aimed at developers with an understanding of ASP.NET MVC and unit tests. I'm not going to cover setting up your project or how to use Visual Studio, read 
[Using TDD with ASP.NET MVC](http://msdn.microsoft.com/en-us/library/ff847525(v=vs.100).aspx) if you need that. 
The MVC application I'm developing consists of a number of similar controllers with a combination of the following GET and POST actions: 
*Create
 
*View 
*Details (Single)
 
*Index (List)
 
*Edit 
*Details (Single)
 
*Index (List)
 
*Delete 
There's nothing particularly unusual about these standard CRUD actions and that's why they're part of the MVC scaffolding. 
I'm taking a consistent approach to controller development so the actions follow the same pattern, typically this means the unit test are also the same. As a result writing unit tests for controllers is very dull and repetitive so I need to find a better way for my own sanity. 
This is particularly true if you want build unit tests for an existing code base or you aren't practising Test-Driven Development (TDD). 
##Detail Action
 
The details action is used in nearly every controller, here's the typical structure

// POST: Teams/Details/5 public ActionResult Details(int? id) { if (id != null) { Team team = FindTeam(id); if (team == null) Danger("The team you were looking for doesn't exist.", true); else return View(team); } return RedirectToAction("Index"); }

Based on what is passed to the controller action I'm expecting one of the following results 
*Return the Team to the Team View
 
*Redirect to the Index
 
*Redirect to the Index with an error 
###Side notes
 
*I'm using the 
[repository design pattern](http://martinfowler.com/eaaCatalog/repository.html) for data access and FindTeam() is used to access the repository
 
*I've implemented alerts using TempData based on 
[James Chambers' post](http://jameschambers.com/2014/06/day-14-bootstrap-alerts-and-mvc-framework-tempdata/), that's what Danger() is all about, although I'm using 
[Foundation](http://foundation.zurb.com) instead of Bootstrap 
##Unit Testing setup
 
First I need to do a bit of setup for my tests, I'm using the built in test framework in Visual Studio 2013 rather than 
[NUnit](http://www.nunit.org) or 
[xUnit](https://github.com/xunit/xunit) and when I setup my solution I also setup a unit test project. 
All I'm doing here is setting up a fake database, putting some data in it and instantiating my controller with the fake database.

[TestClass] public class Controller_Details { private FakePredictDB db; private TeamController controller; [TestInitialize] public void TestInitialize() { db = new FakeDB(); db.AddSet(TeamData.List); controller = new TeamController(db); controller.ControllerContext = new FakeControllerContext(); } }

It's also a good idea to clear up your mess after you're done.

[TestCleanup] public void TestCleanup() { db = null; controller.Dispose(); controller = null; }

###Side notes
 
*I find it useful to use 
[#region](http://msdn.microsoft.com/en-us/library/9a1ybwek.aspx) so I can easily collapse the test setup for example
 
*I've create my own FakeDB which implements the same interface as the real one 
##Fluent MVC Testing
 
After a bit of search I found 
[Fluent MVC Testing](http://docs.teststack.net/fluentmvctesting/), a very nice library that scratched my itch before I went down the route of building it myself. It uses a 
[fluent interface](http://en.wikipedia.org/wiki/Fluent_interface) which helps make the code more readable and also reduces the coding being used. You might have seen this in jQuery where you a chaining multiple actions on a single object and 
[LINQ](http://en.wikipedia.org/wiki/Fluent_interface) makes a lot of use of it too. 
##Verbose test vs. Fluent MVC test
 
As you can see I'm using 
[AAA(Arrange-Act-Assert)](http://www.arrangeactassert.com/why-and-what-is-arrange-act-assert/) test methodology, use it, it'll make your life even easier. 
Next up I want to test the "good path" happens, if I ask for a team that exists does it return the default view? 
###Verbose test


[TestMethod] public void Get_Details_DefaultView() { // Arrange (covered in the setup) // Act ViewResult result = controller.Details(1) as ViewResult; // Assert Assert.IsNotNull(result); Assert.IsNull(view.ViewName); }

###Fluent MVC test


[TestMethod] public void Get_Details_DefaultView() { controller.WithCallTo(c => c.Details(1)) .ShouldRenderDefaultView(); }

##Comparing the tests
 
In the verbose test you need to setup the ViewResult in the 
Act step so it can be used by the 
Assert step and even then testing the default view is returned requires you to check that the result is not null and that the ViewName will be null. 
But it just doesn't read very well, does it? 
It's much easier using WithCallTo to setup the 
Act step and the 
Assert is a simple ShouldRenderDefaultView() method. I like to put line breaks between each of the steps so it's clear what each part of it does. 
IntelliSense is an added bonus as it make writing a new test so much easier. 
##Other tests
 
It won't stop you having to write test the long way but will cover a lot of the most common situations. Those I've come across are: 
*Checking the view returned
 
*Checking the correct model is returned
 
*Checking the an invalid model returns the right result (Model Binding errors) 
The documentation covers a lot more but I hope it gives you a taster.
