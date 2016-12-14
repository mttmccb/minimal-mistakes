---
title: "Renaming a Database in Azure"
tags:
- SQL Server
- azure
---

I couldn't find any way to do it in the Portal so it seems you need to use an alternative, I used

* In the Server Explorer view, expand SQL Databases.
* Right click and Open in SQL Server Object Explorer
* Login, if needed
* Right click the Server (not the database) and Click New Query
* In the Query Window type: `ALTER DATABASE [oldname] MODIFY NAME = [newname]`

My refresh did not work correctly so close Visual Studio and reopen to see the result. Refresh the Azure Portal screen to see the result as well.

Rename Database on Azure - Done.
