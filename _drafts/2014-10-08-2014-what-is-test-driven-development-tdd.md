---
title: What is Test-Driven Development (TDD)?
categories:
- Long
tags:
- csharp
- tdd
- tutorial
---

There have been a lot TDD activity in the the last 6 months and the 
[TDD is dead](http://martinfowler.com/articles/is-tdd-dead/) series of conversations were great for someone new to TDD. 
[Kent Beck](http://en.wikipedia.org/wiki/Kent_Beck) has been credited with developing the technique and 
[wrote the book](http://www.amazon.co.uk/Test-Driven-Development-Addison-Wesley-Signature/dp/0321146530) in 2003.

TDD is a relatively new software development process that emphasises quick feedback, it's summarised by the red/green/refactor mantra. This is simply: 
![](/squarespace_images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_54353a59e4b03c75a8c10f8c_1412774490693__img.png_) 
*Write a failing test (red)
 
*Do some coding to make the test pass (green)
 
*Improve/simplify your code (refactor) 
You then repeat this process, regularly running unit tests to make sure you haven't broken anything along the way. Unit testing is a benefit of TDD but TDD is not just about unit testing.

It's hard to explain TDD effectively without demonstrating it, so I'll walkthrough how this can be done in an C# ASP.NET MVC project.

##Setup


My setup is as follows but you'll need a version of Visual Studio with Unit Testing:

*Windows 7+
 
*Visual Studio 2013 or Visual Studio Express 2013 or Web
 
*An empty project with unit tests added
 
*A basic understand of MVC

##What are you going to implement


For this example we're starting from scratch so we can focus on TDD. Before you start writing your unit tests you need to know what feature you're going to implement, a single feature or algorithm works best.

This could take the form of a user story, I've used the 
[Five Ws](http://en.wikipedia.org/wiki/Five_Ws) format.

###User Story: Team Report


>>>As a Manager in the morning at my desk, I want to view the status of my teams because I want to see how I can improve their performance.


##Arrange, Act, Assert (AAA) pattern


Before I get into how to write the tests I need share a nice pattern to make your unit tests clearer.

*Arrange: Setup the inputs or context for the test, this might involve 
mocks
 
*Act: Execute or start fire the method or action
 
*Assert: Check the output is as expected

Typically I'll enter these statements as 3 comments and group statements accordingly, in some cases either the arrange or assert won't be required but it's hand to have the prompt anyway.

##Red (Fail)


The starting point with TDD is to write a failing test, going back to the user story it looks like we want to display a list of teams. So the first step is to write a failing test, the 
Team Report feature could fail for a number of reasons:

*No records returned
 
*Wrong model return
 
*View returns null
 
*View returns a list

At this stage you want to focus on the test case that best covers the requirement so we'll go with the last one, 
View returns a list.

The test below will:

*Arrange: instantiate the TeamController
 
*Act: fire the Index action and store the result
 
*Assert: check the model return in the result is an IList of Teams.

You'll notice that no code has been written, all you have written is a test with the desired behaviour. To make sure the test fails you can use simply generate an empty class (the Controller) and stub out the method (the ActionResult) then return null to make your test to fail.

The reason we want the test to fail is to show our test works, if it always passes then it's not a very good test.

###First test


[Test Class] public TeamControllerTest { [Test Method] public Get_Index_View_Returns_A_List { //Arrange TeamController = new TeamController(); //Act var result = TeamController.Index(); //Assert var model = result.ViewData.Model as IList&lt;Team&gt;; Assert.IsNotNull(model, "Model should have been a IList&lt;Team&gt;"); } }

###Code


class TeamController : Controller { public ActionResult Index() { return(null); } }

##Green (Pass)
 
Now you have a failing test the next step is to the do the minimum amount of coding to make the test pass. This next step will feel artificial as it's still not doing anything particularly useful but you'd replace

return(null);

with something like this

IList emptyList = new IList&lt;Team&gt;; return(emptyList);

Now rerun the test and it should pass, what this should start to do is to prompt questions like: 
*Where is the data going to come from?
 
*What happens if no data is returned?
 
*What happens a large number of records are returned? 
##Refactor
 
The next step is refactoring, refactoring is the process of improving code, this could be the readability or reducing the complexity. 
In the TDD context this usually means fully implementing the methods you've written tests for and perhaps writing more tests. In this case it could mean doing any or all of the following: 
*Pull data from database into a list
 
*Redirect to a 404 when no records are found
 
*Return a message to the page to display when no records are found
 
*Order and/or filter the data 
Once you've written your original test you will probably need to write additional tests for the other cases as you continue to implement the feature. 
##Repeat
 
Continue developing the feature and run the tests to make sure you haven't broken anything. 
##That's it...
 
That's the basic jist of TDD, I'm going to cover Code Katas soon which can help you get better at the TDD pattern.
