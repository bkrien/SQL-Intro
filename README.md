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

### Task 1: Create and Populate a Table of Bans/Challenges
Based on our conversation from last week, the first thing that you're going to do is create a table that has the rationales for the bans and challenges that the groups developed in class last week. For the sake of simplicity, we're all going to use a standardized list and we're going to assign each of justifications provided a ```ReasonID``` that you can assign to the that you will load in in Task 2. This is the list of justifications that we'll use: 
| BanID | BanName | BanDescription |
|-------|---------|----------------|
| 1 | Violence | Portrayals of physical or psychological violence or trauma |
| 2 | LQBTQ | Portrayal of LGBTQIA+ identities or individuals |
| 3 | Race | Portrayals of racial discrimination, hate, or violence |
| 4 | Profanity | Use of words believed to be profane or obscene |
| 5 | Sexually Explicit | Portrayal or discussion of sex or sex education |
| 6 | Magic | Portrayals of witchcraft, the occult, or the supernatural |

1. To create the ban table, you will use the ```CREATE TABLE``` statement. Enter the following code into the __Schema SQL__ window (top left): 
```
Create Table book_bans (
    BanID int(2),
    BanName varchar(20),
    BanDescription varchar(255)
    );
```
Then hit the "Run" button at the topic of the screen.
> **_NOTE:_** In creating the table, you create each of your fields (BanID, BanName, BanDescription) and then idnetify the type and lenth of data that each of the fields will accept. The BanID field, for instance, will accept an integer that is two digits long (we could have gone with one digit, since our numbers only go through five, but we want to give ourselves room to expand if we need to in the future). The "varchar(20)" denotes that it can accept up to 20 various characters (letters, numbers, and special characters). For more on data types, see: https://www.w3schools.com/sql/sql_datatypes.asp

2. Add the first ban reasion the book_bans table using the ```INSERT INTO``` statement. Enter the following code into the __Schema SQL__ window *below* the code that you entered in the previous step. 
```
INSERT INTO book_bans (BanID, BanName, BanDescription)
VALUES (1, 'Violence', 'Portrayals of physical or psychological violence or trauma');
```

3. Check to see if the data has been correctly added to the database by using the ```SELECT``` statement. Enter the following code in the __Query SQL__ window (top right). 
```SELECT * from book_bans```
If you see your record appear in the __Results__ window at the bottom of the screen, you've entered the information correctly. If not, circle back and make sure that you've entered the previous code exactly and that you've entered everything in the correct windows.  

> **_NOTE:_** The asterisk in the this statement is a __wildcard operator__. In this case it will return all of the records in the a given table, though wildcard operatiors can be used in a number of ways. For more on wildcard operators, see: https://www.w3schools.com/sql/sql_wildcards.asp

4. Enter the remaining book ban records into the book_bans table using the ```INSERT INTO``` statement. Since we're following the exact initial order of the columns, we also don't *need* to include the column names after the ```INSERT INTO``` statement. This time we'll do the remaining four all at once:
```
INSERT INTO book_bans 
VALUES (2, 'LQBTQIA+', 'Portrayal of LGBTQIA+ identities or individuals');
INSERT INTO book_bans 
VALUES (3, 'Race', 'Portrayals of racial discrimination, hate, or violence');
INSERT INTO book_bans 
VALUES (4, 'Profanity', 'Use of words believed to be profane or obscene');
INSERT INTO book_bans 
VALUES (5, 'Sexually Explicit', 'Portrayal or discussion of sex or sex education');
INSERT INTO book_bans 
VALUES (6, 'Magic', 'Portrayals of witchcraft, the occult, or the supernatural');
````

5. In double-checking your work with the ```SELECT * from book_bans``` statement, you notice that there is a mistmatch in the second record, with the BanName as "LGBTQ," while the description uses the acronym "LBTQIA+". To update this upse the ```UPDATE```, ```SET```, and ```WHERE``` statements to update the second record (where the BanID = 2:
```
UPDATE book_bans
SET BanName = 'LGBTQIA+'
WHERE BanID = 2
```

Run the query again with the ```SELECT * from book_bans``` statement in the __Qeary SQL__ window. If you see all five records, you've entered the data and commands correctly and can move onto Task Two. 

### Task Two: Create and Populate a Table of Books
For this taks, you will create a table that will contain the information about your list of 10 books. You should at least __five fields__ in your table, including the title, author, year of the challenge/ban, and the rational for the challence (using the BanID). You can go alter, experiment with, or go beyond the table created in the example, but you are also free to follow the example more closely. Note the by including the BanID, we are creating a way for the tables to link. 

The table that I will create will include the following fields and datatypes: 
* Title: varchar(50)
* Author: varchar(50)
* ISBN: int(13)
* YearOfChallenge: YEAR
* BanID: int(2)

1. Create the table using the ```CREATE TABLE``` statement. You will need to insert this in the __Schema SQL__ window *below where you created the previous table, but above where you began to insert the values into the table.* You can create your own custom table (with at least five fields and the BanID) or follow this example:
```
Create Table books (
    Title varchar(50),
    Author varchar(50),
    OCLC text(9),
  	YearOfChallenge YEAR,
    BanID int(2)
	);
```

2. Populate the table using the ```INSERT INTO``` statement. *You can include this code at the bottom of the __Schema SQL__ window, below where you previously intserted and updated the records for the book ban reasons.* The values that you enter will need to follow the structure of the table you created. For values in the table in Step 1, for instance, I would use this code: 
```
INSERT INTO books
VALUES ('The Hobbit', 'Tolkien, J.R.R.', '1827184', 2001, 1);
```
Enter all ten of your books. You can only select __one BanID__, so pick the one that seems like the best fit (this is a place where controlled vocabularies might be limiting). 

3. Double check that all ten of your books have been entered using the ```SELECT * from books``` statement. __Note__ that in the __Query SQL__ window, you should only have one statement at a time. While you will keep all of the code that you have run together in the __Schema SQL__ window, you will only have one query active at a time. Make sure that you get rid of the query for the book_bans table before running everything. 

If it looks like all your books have been added, congratulations on creating your own database! __Copy or take a screenshot of all of the code in the Schema SQL window and put it into a word document or .txt file. You will upload this as one of the deliverables for this assignment.__ 

You can now proceed to Task Three. 

## Task Three: Querying Data
One of the most powerful features of relational databases is that they allow you to explore large amounts of data very quickly. While you have now created your own database, it is a relatively small one. 

## Additional Resources
W3Schools SQL Resource: https://www.w3schools.com/sql/
