# Introduction to SQL

>### Explaning my understanding of SQL and relational databases.

<br>
</br>

## Firstly, what is meant by SQL?
*(Structured Query Language)*

It's a language that's simple enough to allow both experienced and non expereienced technicals to access, manipulate and do other operations to the data from a relational database.
Plus, SQL has many other databases that support the common standard for the language while also having additional features and storage type that differentiate them from one another and these databases are:
- SQLite
- MySQL
- Postgres
- Oracle
- Microsoft SQL Server

<br>
</br>

## What is meant by relational database?

Basically this database represents a collection of related -hence the name relational- tables, and those tables are made up of rows and coloumns data, and each one of them answers a specific question relating to the big table.

<br>
</br>


Now let's head down to the lessons and exercises:
 
>## [SQL Lesson 1: SELECT queries 101](#SQL-Lesson-1:-SELECT-queries-101)

*In this lesson I was introduced to a query method of SELECT, that's used to retrieve column's data from a SQL database.*

The syntax goes like this:
```
SELECT column's_name
FROM table's_name;
```
But if I wanted to retrieve all the data in the table, I would use the asterisk (*), like this:
```
SELECT *
FROM table's_name;
```
### **Lesson 1 Exercise**
![lesson 1 exercise](/imgs/lesson1exercise.PNG)



<br>
</br>
<br>
</br>

>## [SQL Lesson 2: Queries with constraints (Pt. 1)](#SQL-Lesson-2:-Queries-with-constraints-(Pt.1))

*To avoid getting all the data when retrieving a certain column in a database table, I can use a WHERE, which will help me filter out unneccessary information and only get me the ones that I requested*.
*This also allows the query to run faster due to the reduction in unnecessary data being returned.*

*I can also use logical keywords, such as: AND/OR and other numeric operators, such as:*

| Operator | Condition |
| ----------- | ----------- |
| =, !=, < <=, >, >= | Standard numerical operators	 |
| BETWEEN … AND …	 | Number is within range of two values (inclusive)	 |
| NOT BETWEEN … AND …	 | Number is not within range of two values (inclusive)		 |
| IN (…)		 | Number exists in a list |
| NOT IN (…)	| Number does not exist in a list |


The syntax goes like this:
```
SELECT column's_name
FROM table's_name
WHERE condition
    AND/OR another_condition
    AND/OR …;
```
### **Lesson 2 Exercise**
![lesson 2 exercise](/imgs/lesson2pt1exercise.PNG)

<br>
</br>
<br>
</br>



>## [SQL Lesson 3: Queries with constraints (Pt. 2)](#SQL-Lesson-3:-Queries-with-constraints-(Pt.-2))
*I can filter the text data inside the columns of a table by using operators provided by SQL, and they allow me to do some comparison and matching, amongst other things.*

*And these are the operators:*
| Operator | Condition |
| ----------- | ----------- |
| = | Case sensitive exact string comparison |
| != or <> | Case sensitive exact string inequality comparison |
| LIKE | Case insensitive exact string comparison	 |
| NOT LIKE	 | Case insensitive exact string inequality comparison	 |
| % | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE)	 |
| _ | Used anywhere in a string to match a single character (only with LIKE or NOT LIKE)	 |
| IN (…) | String exists in a list	 |
| NOT IN (…) | String does not exist in a list	 |

### **Lesson 3 Exercise**
![lesson 3 exercise](/imgs/lesson3pt2exercise.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 4: Filtering and sorting Query results](#SQL-Lesson-4:-Filtering-and-sorting-Query-results)
There are more than one clause or keyword to insure that the data we get from the table is filtered out, and those are:

- ### DISTINCT
*To make sure we don't get any duplicated data when aquiring data from the table, we can use the DISTINCT keyword, which makes sure of that by discarding rows that contain duplicate column values.*

The syntax goes like this:
```
SELECT DISTINCT column's_name
FROM table's_name
WHERE condition(s);
```

- ### ORDER BY 
*Because sometimes the data tables contain thousands or million rows, making it difficult to read through them neatly, SQL has a keyword specifically to help out with that; it's ORDER BY which sorts out the results in ascending or descending, avoiding all the misunderstanding that happens when reading from a data table.*

The syntax goes like this:
```
SELECT column's_name
FROM table's_name
WHERE condition(s)
ORDER BY column ASC/DESC;
```

- ## LIMIT and OFFSET
*To make clear which subset of the requested is what we really care about, we use LIMIT and OFFSET clauses, which in turn make sure to reduce the number of rows that are returned and from where exactly to begin extracting those rows, respectively.*

The syntax goes like this:
```
SELECT column's_name
FROM table's_name
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```
### **Lesson 4 Exercise**
![lesson 4 exercise](/imgs/lesson4exercise.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 5: SQL Review: Simple SELECT Queries](#SQL-Lesson-5:-SQL-Review:-Simple-SELECT-Queries)

### **Lesson 5 Exercise**
![lesson 5 exercise](/imgs/lesson5review.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 6: Multi-table queries with JOINs](#SQL-Lesson-6:-Multi-table-queries-with-JOINs)

*In the real world entity data aren't just stored in one table, but rather spread out into mulitple tables, and that makes it difficult to gather all the needed data using only the previous clauses. That's why there are methods to deal with Multi-table queries.*

- ## ***Database normalization***
*It's a design technique that reduces data redundancy and eliminates undesirable characteristics like Insertion, Update and Deletion Anomalies. Normalization rules divides larger tables into smaller tables and links them using relationships. The purpose of Normalisation in SQL is to eliminate redundant (repetitive) data and ensure data is stored logically.*

> Refrence: [What is Normalization in DBMS (SQL)? 1NF, 2NF, 3NF, BCNF Database with Example](https://www.guru99.com/database-normalization.html)


- ## INNER JOIN.
*It helps to connect or match specific row's data from a certain table with another table, given that both of these tables share different information about one single entity. Keeping in mind that there should be a primary/unique key that both of these tables share.*


The syntax goes like this:
```
SELECT column's_name
FROM table's_name
INNER JOIN another_table 
    ON table's_name.id = another_table.id
WHERE condition(s)
ORDER BY column, … ASC/DESC
```

### **Lesson 6 Exercise**
![lesson 6 exercise](/imgs/lesson6exercise.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 13: Inserting rows](#SQL-Lesson-13:-Inserting-rows)

*Rather than quering data from already existing database tables, in this lesson I learnt how to add new data to a schema.*

*Firstly, a schema is basically a visullization of a table and the types of data each column contains*

*Now how to add data into an existing table?*

- ## INSERT
*This statement declares which table I want to add to, and what columns specifically I'm trying to fill, and how many rows exactly I'm going to add or insert (I can add multiple rows).*

The syntax for inserting values for all columns goes like this:
```
INSERT INTO table's_name
VALUES (value_or_expr, another_value_or_expr, …),
       (value_or_expr_2, another_value_or_expr_2, …),
       …;
```

But if I want to add data specifically to certain columns, the syntax changes into this:
```
INSERT INTO table's_name
(column, another_column, …)
VALUES (value_or_expr, another_value_or_expr, …),
      (value_or_expr_2, another_value_or_expr_2, …),
      …;
```

### **Lesson 13 Exercise**
![lesson 13 exercise](/imgs/lesson13exercise.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 14: Updating rows](#SQL-Lesson-14:-Updating-rows)
*In this lesson I learnt how updating already existing data inside a table is done, it's like the old INSERT method when defining what table, columns, rows, but with the exception of updating not adding and using the clause UPDATE with WHERE to add a condition (if we forget the WHERE statement this will cause all the content of the table to be updated), also for extra care, use the SELECT method*

*One other important thing is making sure that the new updated data match the data type of the content of the schema.*

The syntax goes like this:
```
UPDATE table's_name
SET column = value_or_expr, 
    other_column = another_value_or_expr, 
    …
WHERE condition;
```

### **Lesson 14 Exercise**
![lesson 14 exercise](/imgs/lesson14exercise.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 15: Deleting rows](#SQL-Lesson-15:-Deleting-rows)
*Now to delete certain data from a table, I use the DELETE statement with a WHERE statement to make sure it satisfy a condition in order not to delete all the content of the rows by accident. And for extra care, just like witht the UPDATE statement, it's better to use it with a SELECT method*

The syntax goes like this:
```
DELETE FROM table's_name
WHERE condition;
```

### **Lesson 15 Exercise**
![lesson 15 exercise](/imgs/lesson15exercise.PNG)



<br>
</br>
<br>
</br>


>## [SQL Lesson 16: Creating tables](#SQL-Lesson-16:-Creating-tables)
*When wanting to create a new entity that doesn't exist in the database I can use the CREATE TABLE statement with the extra IF NOT EXISTS just to make sure that what I'm creating is in fact new.*
*Keeping in mind that there are various data types that I have to abide by when creating a table, in addition to certain constraints as to limit the amount of values to be inserted into each column.*

The syntax goes like this:
```
CREATE TABLE IF NOT EXISTS table's_name (
    column DataType TableConstraint DEFAULT default_value,
    another_column DataType TableConstraint DEFAULT default_value,
    …
);
```

### **Lesson 16 Exercise**
![lesson 16 exercise](/imgs/lesson16exercise.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 17: Altering tables](#SQL-Lesson-17:-Altering-tables)
*As to make sure I can keep up with the changes that happen to the data over time, I can use the ALTER TABLE statement which helps me by updating the tables in the database schemas, by adding, removing, modifying.*


- ## ADDING COLUMNS
*It's just like when creating a table but I have to be extra careful with specifying the exact columns and the data types, sometimes with additional constraints, whilst using the ADD statement.*

The syntax goes like this when adding new columns:
```
ALTER TABLE table's_name
ADD column DataType OptionalTableConstraint 
    DEFAULT default_value;
```

- ## REMOVING COLUMNS
*Some databases support removing whole columns from a certain table, others don't, but it's still follows the previous rules with using DROP statement.*

The syntax goes like this:
```
ALTER TABLE table's_name
DROP column_to_be_deleted;
```

- ## RENAMING THE TABLE
*To rename an already existing table, I can do so by using RENAME TO statement.*

The syntax goes like this:
```
ALTER TABLE table's_name
RENAME TO new_table_name;
```

### **Lesson 17 Exercise**
![lesson 17 exercise](/imgs/lesson17exercise.PNG)


<br>
</br>
<br>
</br>


>## [SQL Lesson 18: Dropping tables](#SQL-Lesson-18:-Dropping-tables)
*To remove a table schema entirely from the database, I don't just use the DELETE statement but rather the DROP TABLE, as it makes sure of that.*
*Making sure to use IF EXISTS statement to be extra careful in order to not get an error if the table I want to drop doesn't actually exist.*

The syntax goes like this:
```
DROP TABLE IF EXISTS table's_name;
```

### **Lesson 18 Exercise**
![lesson 18 exercise](/imgs/lesson18exercise.PNG)