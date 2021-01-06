### 301 Reading Notes

## Class -08


## SQLBolt

- what is SQL? Structured Query Language. Designed to allow both technical and nontechnical users query, manipulate, and transform data from a relational database. 

- Due to it simplicity, SQL databases are safe and scalable storage that are used my most big brands.

-  A relational database represents a collection of related (two-dimensional) tables.

# SELECT queries 101

- to retrieve data from a SQL database, we need to write SELECT statements, which are often colloquially refered to as queries.

- A query is a statement which declares what data we are looking for, where to find it in the database, and optionally, how to transform i before it is returned.



```
SELECT column, another_column, ...
FROM mytable;
```
would select a query from each specific column

```
SELECT *
FROM mytable;
```
would select all query from all columns

to run constraints, use

```
SELECT title, year FROM movies WHERE year < 2000 OR year > 2010;
```

- When using the WHERE clause , SQL supports many useful operators to do things like case-insensitive string comparison and matching.

- All strings must be quoted so that the query parser can distinguish words in the string from SQL keywords.

- 

```
SELECT title, director FROM movies
WHERE director != "John Lasseter";
```

