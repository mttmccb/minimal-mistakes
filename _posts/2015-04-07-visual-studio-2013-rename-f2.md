---
title: 'Visual Studio Shortcut: Rename Refactoring (Ctrl+R, R)'
tags:
- Short
- Visual Studio
- Shortcut
- Productivity
- Refactoring
redirect_from:
- /blog/2015/visual-studio-2013-rename-f2
---

Although I've been doing a lot of refactoring with 
[ReSharper](https://www.jetbrains.com/resharper/) lately as I 
[mentioned](http://mttmccb.net/blog/2015/resharper) a few weeks ago, the built-in Visual Studio behaviour is still pretty good.

If you don't know what I'm talking about then I may be about to make your life easier and it might have been something you shied away before because you thought it was hard to do.

Before you do any refactoring you might want ask yourself a few of these questions? I'd recommend a combination of the following steps:

*When did you last check your code into source control?


*Should you create a new branch for the refactoring? Maybe overkill, but good practice.


*Is the code you're changing cover by unit tests? If you make a change it's good to know it hasn't broken anything that was working.

With that in mind let's get on with it.

Suppose a previous developer decided that using 
i for a variable name was helpful (HINT: it's not) and you want to rename it something more meaningful so the code is readable. Place the cursor on the variable and press 
**Ctrl + R, R**
, then you'll get this nice popup asking you to enter a new name: 
![](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_5522e0a2e4b09b97d697a3b0_1428349091977__img.png)You'll see you have the option to search in comments and search in strings which may be useful. I find search in strings often caused more problems so be careful when you are doing this one. By it's nature if you're using strings then the compiler probably won't warn you when you broke something. In this case some well placed unit tests will help ensure your refactoring doesn't break anything.

But as you can see you can Preview the changes before you make them on the next screen.

It's worth noting you're not doing Find and Replace, it won't change every 
i to 
number just those referenced by the symbol you're renaming. 
![](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_5522e197e4b00f941acabdf7_1428349336245__img.png)Press enter or click apply and it's done. 
![](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_5522ecbee4b0983c73d9c28d_1428352190865__img.png)This is a simple example but the process is the same for more far reaching refactorings. As well as local variables you can rename Fields, Namespaces, Types, Properties and Methods.

Happy Renaming!
