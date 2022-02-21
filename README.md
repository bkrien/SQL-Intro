# Introduction to Structured Query Language (SQL)
In this lab, you will explore using the Structured Query Language (SQL, pronounced "sequel") to add, organize, and search through data by __creating your own SQL database__ of the banned book data that you've been developing and working with in class to this point. 

## What You'll Do
1. Create and connect tables in using SQL
2. Set the data types for the values in your tables
3. Add data to populate the tables 
4. Create queries to return records meeting specific criteria

## Why It Matters
SQL is one of the most common and most powerful ways to create, manage, and query data in a relational database. While most librarians don't need to master SQL in order to do their work, understanding how SQL works and, by extension, how relational databases are created, managed, and used is useful knowledge for those working in libraries or in any field that involves the organization of information.

We'll just be scratching the surface of what you can do with SQL in this lab. Anyone interested in learning more about SQL and relational databases should consider taking [SLIS 6100: Database Management](https://catalog.registrar.uiowa.edu/graduate-college/library-information-science/#:~:text=SLIS%3A6100%20Database%20Management)

## Instructions
### DB Fiddle
For this lab, we'll be using a free, online database tool called [DB Fiddle](https://www.db-fiddle.com/). This tool will allow you to create and explore a small database using SQL, without the need to download any software or access a special server setup. DB Fiddle is useful because on a single screen it allows you to see the __Schema SQL__ (in the top left) that allows you to create and manipulate the data, the __Query SQL__ (in the top right) that allows you to control which results from this data are returned, and these __ Results__ (along the bottom). 

You can see what this looks like with an example that creates a small Persons tables, adds a person, and then returns the resulting person along the bottom:
![DB Fiddle Example](/screenshots/DB_Fiddle_Homescreen.png)

As you go through the process of 

### Task 1: Create a Table of Bans/Challenges
Based on our conversation from last week, the first thing that you're going to do is create a table that has the rationales for the bans and challenges that the groups developed in class last week. For the sake of simplicity, we're all going to use a standardized list and we're going to assign each of justifications provided a ```ReasonID``` that you can assign to the that you will load in in Task 2. This is the list of justifications that we'll use: 
| BanID | BanName | BanDescription |
|-------|---------|----------------|
| 1 | Violence | Portrayals of physical or psychological violence or trauma |
| 2 | LQBTQIA+ | Portrayal of LGBTQIA+ identities or individuals |
| 3 | Race | Portrayals of racial discrimination, hate, or violence |
| 4 | Profanity | Use of words believed to be profane or obscene |
| 5 | Sexually Explicit | Portrayal or discussion of sex or sex education |

1. To create the ban table, you will use the ```CREATE TABLE``` statemtn. Enter the following code into the __Schema SQL__ window (top left): 
```Create Table book_bans (
    BanID int(2),
    BanName varchar(20),
    BanDescription varchar(255)
    );
```



## Additional Resources
W3Schools SQL Resource: https://www.w3schools.com/sql/
