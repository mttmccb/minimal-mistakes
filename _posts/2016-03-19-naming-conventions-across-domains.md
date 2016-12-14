---
title: Naming conventions across domains
tags:
- ASP.NET
- JavaScript
- SQL Server
---

Sometimes it’s nice to join things together and while these aren’t really big changes on their own they make you and your team’s life much easier. In short use the conventions of the domain you’re working in. Here are some tips on what I’ve done to make my life easier. 
Just to get a few definitions out of the way when it comes to naming conventions 

* **snake_case**
  - words are separated by underscores. SQL uses this because most database store them in uppercase anyway.
* **kebab-case**
  - words are separated by dashes. You’ll see this use in CSS a lot.
* **PascalCase**
  - word are combined but the first and subsequent first letters of each word are in uppercase. C# predominantly uses PascalCase.
* **camelCase**
  - Similar to PascalCase but the first letter isn’t uppercase. JavaScript uses this. 

## Database objects, in my case **SQL Server**
 
As I mentioned snake_case is pretty common when naming objects wether that’s tables, field or stored procedure names. However I tend to stick to using PascalCase for naming variables, this might be because using Database Projects. I’m sure there’s a good reason not to do this too but I haven’t come across it yet. 

## Database to Data Access in my case **Dapper (C#)**
 
I’m sure there similar options in other object mappers but in 
[Dapper](http://stackexchange.github.io/dapper-dot-net/) you just turn on an option and your underscores will be remove and your fields mapped (assuming you have the types matched up ok). 

```csharp
Dapper.DefaultTypeMap.MatchNamesWithUnderscores = true;
```

## Data Access to Database
 
I haven’t found an easy way to do this in the other direction so I tend to use PascalCase. It’s probably something I need to try out. 

## Data Access to Front End, in my case **JavaScript**
 
camelCase is most common naming convention in JavaScript and when passing data from your data access layer it’s likely it’s going to be PascalCase or maybe even snake_case (I hope you’re not accessing your database directly from the front end!). I was originally going to share a quick way to achieve this by adding custom 
JsonProperty’s but that would quickly become painful 

```csharp
public class Person { 
  [JsonProperty(“fullName”)] 
  public string FullName { get; set; } 
}
```

Instead you can use something like a 
[ContractResolver](http://www.newtonsoft.com/json/help/html/contractresolver.htm) 

```csharp
JsonConvert.SerializeObject( &lt;YOUR OBJECT&gt;, new JsonSerializerSettings { ContractResolver = new CamelCasePropertyNamesContractResolver() });
```

## Front End to Data Access
 
I haven’t had a problem here, perhaps this was already anticipated in the method I’m using to pass data.
