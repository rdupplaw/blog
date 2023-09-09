---
title: "Week 4 at Makers"
date: 2021-05-23
tag: makers diary
---

This week we began integrating databases into our web applications for data persistence. We looked at ways of designing a database structure for an application given specifications and user stories.

## Designing web apps with databases

Most applications start with specifications. This might be something like "the website should show a list of posts" or "the website should let you sign in." You can move from specifications to user stories, which take the form "As an x, so I can y, I want to z." For example: As a user, so I can stay up to date, I want to see a list of posts in reverse chronological order.

User stories help you to write acceptance tests or feature tests. These test the overall functionality of the application. To pass these, you need to design the model layer of the model-view-controller (MVC), which will in turn require unit tests. 

This is where Class Responsibility Collaborator (CRC) cards come in useful. CRC cards allow you to quickly design the objects in an application by writing down the classes, their responsibilities and which other objects they collaborate with. This allows you to do the minimum amount of design required before you start writing unit tests and actual code.

The objects of your application are closely related to the database structure. Knowing the attributes of each class pretty much gives you the columns of each table, and the collaborations you've identified offer hints about relationships between tables (e.g. "a user has many posts, a post has one author" or "a post has many tags, a tag has many posts". In the latter case, you will need a join table to connect each post with each tag applied to it, and each tag with each post it's applied to). 

Object-relational mappers can map the data from the database into an object in your program, and you can add any desired logic into the object thus created. Conventional RESTful route naming makes the function of each route clear, and ERB templates can dynamically render your data in HTML.