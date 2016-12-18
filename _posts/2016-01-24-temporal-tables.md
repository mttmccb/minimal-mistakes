---
title: "SQL Server 2016 Temporal Tables"
tags:
- SQL Server
- Temporal Tables
header:
  image: /images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_56a535f3fd5d084f324deb97_1453667828576_37376926_054c123262_b.jpg
  caption: "Source: Nick Dimmock"
---

I first heard about Temporal Tables when it was mentioned in a 
[Channel 9](http://channel9.msdn.com/Shows/Data-Exposed/Temporal-in-SQL-Server-2016) video with Scott Klein and Borko Novakovic early last year. To be honest I was a little surprised it wasn't already in place but after finding out more I was annoyed it wasn't available until SQL Server 2016. Ah well.

In short, you flip a switch on a table to make it a temporal and you can access it at any point in time. No messing around with triggers or updating your stored procedures.

Born SQL did a great 4-part series last year which are all worth a read

* [An Introduction to Temporal Tables in SQL Server 2016 using a DeLorean](https://bornsql.ca/2015/11/introduction-temporal-tables-sql-server-2016-using-delorean/)
* [Temporal Tables Under The Covers](https://bornsql.ca/2015/11/temporal-tables-under-the-covers/)
* [Modifying Temporal Tables – A Primer](https://bornsql.ca/2015/11/modifying-temporal-tables/)
* [Temporal Tables – When To Use Them](https://bornsql.ca/2015/12/temporal-tables-when-to-use-them/)

The only part I wish were possible was to make it easy to push changes into the future, but that could get messy. This also touches on one of my main gripes when describing these kind of features and that's relating them to time travel. Maybe it's just me but I always think of time travel as a way to travel into the future as well as the past. Audit logs or history tables don't really work like that. Perhaps a better way might be to think of each history table as a stack of incredibly tedious and repetitive journals? 

However as SQL Server 2016 isn't available in any of the projects it's just something I'll keep an eye on and get a better understanding of it. Until then I'll be stuck with doing it my stored procedures.
