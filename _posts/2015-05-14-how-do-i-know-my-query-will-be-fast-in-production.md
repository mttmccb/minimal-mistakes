---
title: How Do I Know My Query Will Be Fast In Production?
categories:
- Short
tags:
- SQL Server
---

Another 
[great post](http://www.brentozar.com/archive/2015/04/how-do-i-know-my-query-will-be-fast-in-production/) from Jeremiah Peschka over on Brent Ozar Unlimited. I'll need to make use of 
[statistics parser](http://statisticsparser.com). 
I've been making a lot of use of 
STATISTICS IO but I don't really believe what 
STATISTICS TIME tells me as it changes fairly often. 
MCR and BCR new concepts for me and they'll be useful but getting a sense of how many logical reads is slow for our setup will be most useful. However environments differ so testing them is always going to be useful.
