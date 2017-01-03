---
title: SQL Server Table-Valued Parameters for Stored Procedures
tags:
- Long
- TVP
- SQL Server
- Stored Procedure
---

![Source: BizarreBytes](/images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_55203d7ae4b0f9cd71b4e2c5_1428176251127__img.jpg) Source: BizarreBytes 
So you need to pass multiple values to a stored procedure? Well you don't have too many great options but 
[Table-Valued Parameters](https://msdn.microsoft.com/en-us/library/bb510489.aspx) (TVPs) are a good way of doing it. 
##Why send a table anyway?


You probably want to reduce network traffic and do all the work you need to do with your data all at once. It would be nice if your table was strongly typed too because that's one less thing to worry about, right? As most of what I do starts in C# my data is already strongly typed so it's even easier. Let's assume you've mapped your objects to your to stored procedure, in my case I've used 
[Dapper](https://github.com/StackExchange/dapper-dot-net) but I'll cover that in another post.

##Can I see how you'd it?


Let's take a fairly simple example, saving items that you want to tag. To do this suppose your UI generates a list like this:

Id Tag 1 Carrots 2Sprouts 3Bananas -1Dragon Fruit

And you want pass this table of Ids and Tags to your stored procedure. I'm using -1 to indicate a new item and the others already exists so maybe they're being edited.

##How do I create a TVP?


First you need to create the table-valued parameter type that matches the structure of your data. In this case

CREATE TYPE TagTableType AS TABLE ( Id INT NOT NULL, Tag VARCHAR(50) NOT NULL); GO

Because I know I'm going to have an Id and a Tag I'm going to be make sure of it by using 
NOT NULL. 
##How do I use a TVP?
 
First we need to create a stored procedure to use the TVP. You'll notice it's declared as READONLY, this isn't optional. If you want to change the TVP then you need to put it into a temp table or table variable. In this case I'm using a merge statement to do the UPDATE and INSERTs.

CREATE PROCEDURE dbo. usp_InsertTags @TVP TagTableType READONLY AS SET NOCOUNT ON MERGE INTO [dbo].[Tags] AS target USING @TVP AS source ON target.Id = source.Id WHEN MATCHED THEN UPDATE SET target.TagName = source.TagName WHEN NOT MATCHED BY TARGET THEN INSERT (TagName) VALUES (source.TagName); GO

Then when it comes to using it we first need to declare a variable of that type

DECLARE @TagTVP AS TagTableType;

Put some data in it, just like a regular table

INSERT INTO @TagTableType (Id, Tag) VALUES(1, 'Carrots'); INSERT INTO @TagTableType (Id, Tag) VALUES(2, 'Spouts'); INSERT INTO @TagTableType (Id, Tag) VALUES(3, 'Bananas'); INSERT INTO @TagTableType (Id, Tag) VALUES(-1, 'Dragon Fruit');

And finally execute the stored procedure using the TVP.

EXEC usp_InsertTags @TagTVP; GO

It's that simple, and even simpler if you have a look the 
[sqlfiddle](http://sqlfiddle.com/#!6/70efc/1/0) I put together. 
##Limitations
 
TVPs are just tables so you can't construct complex objects, well not easily. You can use XML fields if you really want to but I'll go through that in another post, I'm still not sure that's a good idea. Also 
[SQL_VARIANT](https://msdn.microsoft.com/en-us/library/ms173829.aspx) is a no-no but I've never used them myself, they don't look like a good idea to me. 
[Follow my blog with Bloglovin](http://www.bloglovin.com/blog/13928111/?claim=eamvbby3wnt).
