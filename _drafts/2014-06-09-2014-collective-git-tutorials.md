---
title: Collective Gits
categories:
- Long
tags:
- git
- bitbucket
- csv
- dcsv
- software development
---

[![](/squarespace_images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_53956fdfe4b05b6ed482d9cd_1402302432246__img.png_)](http://git-scm.com)I'm trying to turn myself into an expert on 
[Git](http://git-scm.com/), the popular distributed version control system (DVCS). I'll hopefully share what I learned when I've used it a lot more. I have a long way to go before I can call myself an expert, probably about another 9,900 hours according to 
[Malcolm Gladwell](http://www.amazon.co.uk/Outliers-Story-Success-Malcolm-Gladwell/dp/0141036257).

To get myself there I need to turn to the wisdom of others, it's still a relatively new system as it was originally released in April 2005 but is becoming the de facto standard in software version control. Looking at a lot of job adverts recently have shown that and according to 
[ITJobsWatch](http://www.itjobswatch.co.uk/jobs/uk/git%20%28software%29.do) it's listed as a requirement for 18.13% (3 months to 9 June 2013) of software development jobs up from 6.93% (Same period 2012).

##Learning Git the hard way


While it's possible and probably preferable to use Git with a GUI, I'm going to focus on learn Git using the command line tools where possible. This will probably be hard but I'm hoping it will also cement the concepts in my head more than just picking up a GUI would. I won't completely reject GUIs, that would be stupid but I will 
favour the command line, for now.

What follows might not make sense if you haven't done anything on Git so I'd suggest diving right into one of the resources I'm going to recommend.

##Train like a Git


My learning style definitely favours 
doing rather than reading. The good thing about the various training options out there is that they also favour this approach.

###[Git For Ages 4 and Up (Video)](https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCgQFjAA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D1ffBJ4sVUb4&ei=i3aVU6maJIeVPOyHgZAF&usg=AFQjCNF3f4P-Uk8ZYj-xy173AXvPoH-Oww&bvm=bv.68445247,d.ZWU) by Michael Schwern


It you have a fondness for dungarees and beard stroking you're in luck, the bonus is that it's a realitively painless way to learn the importance of the basics of Git. The two that stuck out for me are:

*Commits are unique 
*You can't change them


*They contain the author, date/time and previous commit


*HEAD, Branch, Master, Origin, Commit ID, v1.1 are all just pointers and can be used in the same way 
*Well tags can be moved but apart from that...

###[Explain Git with D3](http://www.wei-wang.com/ExplainGitWithD3/)


Wei Wang created a visual approach to learning Git he's used SVG and D3 to create interactive tutorials as well as a free playground. You don't even need to install Git as you can do it all from the browser. Similar to Git For Ages 4 and Up this combines the command line with a visual look at what's going on with the repository when you 
do stuff which is very handy.

It doesn't cover the commands in massive detail so it's a good entry point.

###[Git Immersion](http://gitimmersion.com)


Quite a simple walkthrough that is split up to make it easy to stop and start at any point. It also includes a sample project to use to demonstrate the concepts.

###[Think like (a) Git](http://think-like-a-git.net)


I have only just started on this one but I like the writing style, like Git Immersion it's split into easily digestable chunks, mmm tasty chunks.

###[Pro Git (Online Book)](http://git-scm.com/book)


This was the first tutorial I went through, actually it's a book and a pretty comphrensive one at that. I wouldn't recommend you look at this one first but do it soon after you understand the basics. Some of the language and examples I found to be a little too complicated but it's worth reading.

###[Try Git](https://try.github.io/)


Recommended by Git, I haven't been through this one yet.

###[Git Tutorials and Training (Atlassian)](https://www.atlassian.com/git)


I haven't used SVN but it would be useful to understand how you would migrate from that. Atlassian cover this and a number of common workflows.

##Battering the Git into my brain


I plan to revisit some of these tutorial but there's no substitute for regularly using Git. As Git can be used in a number of different scenerios I'm trying to use it for those including: 
[![](/squarespace_images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_539595d9e4b05bede087eaae_1402312154126__img.png_)](http://bitbucket.com) 
[![](/squarespace_images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_53959567e4b05bede087ea44_1402312039947__img.png_)](http://github.com)***A private repository:**
 My CV is now kept in a Git repository, it's not code but Git can really be used for an file. Ideally I'd like to get my CV in a markdown format and convert it PDF / Docx format as the last step. This might make things like the diff tools and merge slightly more interesting. I'll probably put this in a 
[BitBucket](http://github.com) repository and eventually share a copy on this site.


***A public repository:**
 I'm looking for a coding project, probably a combination of everything I've learned which I can then share on 
[GitHub](http://bitbucket.com).


***Forking an existing project:**
 This will help teach me how to use more of the collaborative features and how to make use of pull requests which both BitBucket and GitHub use.

I'd also like to put together my own cheat sheet of what I use and have found, particularly some of the aliases and 'tricks' that make things a little easier.

##Final thoughts


Coming from an engineering background like myself you aren't exposed to CVSs but what Git has shown me is that anyone could benefit from using it. Git doesn't care what you put in it. It would be great for designers who need to keep copies of old mockups and designs.

If you have found or created better Git resources than those above please let me know.
