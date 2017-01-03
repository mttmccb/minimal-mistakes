---
title: 'Visual Studio Shortcut: Extract Method (Ctrl+R, M)'
categories:
- Short
tags:
- Shortcut
- Visual Studio
---

[Rename Refactoring](http://mttmccb.net/blog/2015/visual-studio-2013-rename-f2) and Extract Method are definitely the refactorings I do the most so it's well worth learning the shortcuts. Extract Method is a little trickier than rename but it can have a bigger impact on the readability of your code. 
Suppose you have a method you'd like to make a little clearer, let's call it the Method of Doom, it could be a few screens long or it could just be overly convoluted. The following method is very simple but will demonstrate the theory. The method just returns a parsed number, but if it's negative then it throws an exeception, it's an extract from one solution to the 
[string calculator](http://osherove.com/tdd-kata-1/) 
[code kata](http://mttmccb.net/blog/2014/edge-cases-of-tomorrow?rq=code%20kata).

private static int ReturnOneNumber(string number) { int numberAsInt = int.Parse(number); if (numberAsInt < 0) throw new Exception("negatives not allowed"); return numberAsInt; }

The section that handles the checking of the negative number could be clearer, so lets make it so. First highlight that section of code, then press 
**Ctrl+R, M**
 and you'll get a dialog box to give it a name. 
![](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_55453081e4b03d21cf467e23_1430597762287__img.png) 
And then the resulting code will be look something like this.

private static int ReturnOneNumber(string number) { int numberAsInt = int.Parse(number); HandleNegatives(numberAsInt); return numberAsInt; } private static void HandleNegatives(int numberAsInt) { if (numberAsInt < 0) throw new Exception("negatives not allowed"); }

Of course this is a very small example, but imagine a very long method that you can clean up by performing multiple extract method refactorings. Not only will it be easier to understand but you might find it easier to simplify if, which may not have been the case with the Method of Doom.
