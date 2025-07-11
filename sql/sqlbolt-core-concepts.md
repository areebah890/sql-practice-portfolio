## SQLBolt Practice: Lessons 1–6
Areebah , July 2025
-- Description: SQL practice covering SELECT, WHERE, AND/OR, ORDER BY, INSERT, and UPDATE. 
All lessons provided interactive tasks that allowed me to practice and showcase skills I'm learning  

## SQL = Structured Query Language 
-- Designed to allow users to query, manipulate and transform data from a rational database
-- Rational database = represent collection of 2D tables with a fixed number of named columns (the attributes or properties of the table) and any number of rows of data
-- The goal is to learn how to answer specific question's about a data set to help us make better decisions down the road.

## Lesson 1 : SELECT Queries 
-- SELECT statements (aka queries) are used to retrieve data from SQL database
-- Query = a statement that declares what data we are looking for, where to find it in the database, how to transform it before it is retured

---- Select Query for specific columns
SELECT column1, column2, ...
  FROM table; 
~ SELECT title FROM movies; => this would return the column title from the table named movies 
  
----Select Query for all columns 
SELECT * 
FROM table;
~ This would return all columns from the table 

## Lesson 2 : Queries with Constraints
-- SELECT allows us to select specific columns of data from a table but if the table has millions of rows of data it would he inefficient
-- in order to filter certain results from bienf returned we use WHERE clause in our query
-- this clause is applied to each row if data checking specific column values to determine whether it should be included in the reults 

---- Select query with constraints
SELECT column1, column2, …
FROM table
WHERE condition1
    AND/OR condition2
    AND/OR …;
~ this allows us to set conditions to the data we want returned 


# Useful operators for numerical data (ie. integer or floating point):

| Operator              | Condition                                      | SQL Example                      |
|-----------------------|------------------------------------------------|----------------------------------|
| =, !=, <, <=, >, >=   | Standard numerical operators                   | `col_name != 4`                  |
| BETWEEN … AND …       | Number is within a range (inclusive)           | `col_name BETWEEN 1.5 AND 10.5`  |
| NOT BETWEEN … AND …   | Number is *not* within a range (inclusive)     | `col_name NOT BETWEEN 1 AND 10`  |
| IN (…)                | Value exists in a list                         | `col_name IN (2, 4, 6)`          |
| NOT IN (…)            | Value does not exist in a list                 | `col_name NOT IN (1, 3, 5)`      |

## Lesson 3 : Queries with Constraints pt.2
-- SQL supports useful operators for case insesitive string comparison and wildcarn pattern matching 

| Operator       | Condition                                               | Example                             |
|----------------|----------------------------------------------------------|-------------------------------------|
| =              | Case-sensitive exact string comparison                  | `col_name = "abc"`                  |
| != or <>       | Case-sensitive exact string inequality comparison       | `col_name != "abcd"`                |
| LIKE           | Case-insensitive pattern match                          | `col_name LIKE "ABC"`               |
| NOT LIKE       | Case-insensitive pattern mismatch                       | `col_name NOT LIKE "ABCD"`          |
| %              | Matches zero or more characters (used with LIKE/NOT LIKE) | `col_name LIKE "%AT%"` (matches `"AT"`, `"ATTIC"`, `"CAT"`, `"BATS"`) |
| _              | Matches a single character (used with LIKE/NOT LIKE)     | `col_name LIKE "AN_"` (matches `"AND"`, not `"AN"`) |
| IN (…)         | String exists in a list                                 | `col_name IN ("A", "B", "C")`       |
| NOT IN (…)     | String does not exist in a list                         | `col_name NOT IN ("D", "E", "F")`   |

## Lesson 4 : Filtering and Sorting Query Results
-- The data in a database may be unique but the result of a particular query may not be E.g movies being released in the same year

---- Select query with unique results
SELECT DISTINCT column1, column2, …
FROM table
WHERE condition(s);
~ DISTINCT discard rows that have a duplicate column
this blindly removes duplicate rows but can use GROUP BY clause to specify rows - more on this later 

---- Ordering data 
most real databases have data added in no particular order which is difficult to read through and understand, SQL can sort the results in ascenidng ot descending order
ORDER BY clause 

SELECT column1, column2, …
FROM table
WHERE condition(s)
ORDER BY column ASC/DESC;
~ each row is sorted alpha - numerically based on specified columns 

---- Limiting results to a subject 
SQL provides clauses commonly used with ORDER BY useful in optimisation to indicate to the database the subset of the result we want
LIMIT will reduce the number of rows to return, and optional OFFSET will specify where to begin counting the number rows from.

SELECT column1, column2, …
FROM table
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;

