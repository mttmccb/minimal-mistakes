---
title: Dappling with Dapper .Net Part 1 - Why?
categories:
- Long
tags:
- Dapper
- DAL
---

Tell your DBA that you're going to be using an ORM like Entity Framework (EF) and they'll probably cry. Performance is going to be impacted negatively. Your DBA probably spent some time optimising and tuning the database and you just kicked them in the nuts by add overhead to every request. 
I'm sure you were doing it because you could develop faster with an ORM and you didn't want to get your hands dirty with stored procedures or raw SQL. That's understandable but I'd rather play to the strengths of a domain-specific language like SQL. 
Using an ORM is a lot like relying on jQuery, 
[you might not need jQuery](http://youmightnotneedjquery.com) and you probably don't need a lot of the features of an ORM. A Micro-ORM might work for you. 
##Micro-ORM?
 
The problem I'm trying to solve is to quickly map a database object to a 
[POCO](http://en.wikipedia.org/wiki/Plain_Old_CLR_Object), the ORM deals with converting between incompatible types. Ideally it will give you a 1:1 mapping between tables and objects. I can deal with the CRUD operations in SQL so I don't really need the ORM to do that. 
This is where Micro-ORMs come in, if you're looking for a comparison then Andrew West covered 
[Dapper](http://andrewtwest.com/2012/08/19/micro-orms-for-net-compared-part-1/), 
[Massive](http://andrewtwest.com/2012/08/20/micro-orms-for-net-compared-part-2/) and 
[PetaPoco](http://andrewtwest.com/2012/08/21/micro-orms-for-net-compared-part-3/) a few year ago. 
I've chosen to go with 
[Dapper](https://github.com/StackExchange/dapper-dot-net) because it's focussed on performance and 
[slow pages damage how users perceive your content, design and navigation](http://calendar.perfplanet.com/2013/slow-pages-damage-perception/) so it should be a priority for you. Also it's very close to the performance you'd get using more manual 
SqlDataReader approach as you can see from one of the performance benchmarks below.

Method 
Duration 
Hand coded (using a 
SqlDataReader) 
47ms 
Dapper 
ExecuteMapperQuery 
49ms 
ServiceStack.OrmLite (QueryById) 
50ms 
PetaPoco 
52ms 
BLToolkit 
80ms 
SubSonic CodingHorror 
107ms 
NHibernate SQL 
104ms 
Linq 2 SQL 
ExecuteQuery 
181ms 
Entity framework 
ExecuteStoreQuery 
631ms

##The hard way: SQLDataReader


I'd recommend you have a look at how to do things with 
SqlDataReader as some of the concepts are similar, the main one being you're dealing with a stream of data so order is important. 
![Well, I don't want Fop, goddammit. I'm a Dapper Dan man](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_55468c33e4b0a1a9a9ffdf0e_1430686796013__img.gif) Well, I don't want Fop, goddammit. I'm a Dapper Dan man 
##Why use Dapper?
 
Apart from the performance? Well, it's been well tested by 
[StackOverflow](http://stackoverflow.com) and it's pretty mature now. 
[Sam Saffron](http://samsaffron.com) wrote about how he came to 
[write his own ORM](http://samsaffron.com/archive/2011/03/30/How+I+learned+to+stop+worrying+and+write+my+own+ORM) and his challenges with LINQ-2-SQL. Although he has now left StackOverflow it appears to be actively maintained by 
[Marc Gavell](http://blog.marcgravell.com) and available for free under the Apache Licence 2.0 or MIT Licence. 
###My use case
 
It worth mentioning my main use case doesn't really fit with the original purpose of Dapper but luckily as time passed full support for stored procedures has been added. 
###Main features of Dapper
 
Of course 
object mapping is the main feature but it also supports 
lists, 
buffering, 
mapping to multiple object, 
dealing with multiple result sets and all that while being 
database independent. 
[Matt Roberts](http://matt-roberts.me/post/dapper) uses mysql and I use SQL Server without any problems. 
###It's not perfect
 
But that's fine, nothing is. The documentation is a bit ropey, but I hope to cover some of the discoveries I've made. Unfortunately it relies too much on the unit tests as a means of documenting the features and, of course, asking the right questions on StackOverflow. 
##Next Up...
 
Dapper is just a single file you can drop into your project and it's really easy get up and running. I'll cover more in the next 
**Setup**
 post.
