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

- the DISTINCT keyword will remove duplicate rows.

- you can use the ORDER BY key word to organize the results of the query.

- When an ORDER BY clause is specified, each row is sorted alpha-numerically based on the specified column's value. In some databases, you can also specify a collation to better sort data containing international text.

- Another clause which is commonly used with the ORDER BY clause are the LIMIT and OFFSET clauses, which are a useful optimization to indicate to the database the subset of the results you care about.
The LIMIT will reduce the number of rows to return, and the optional OFFSET will specify where to begin counting the number rows from.

```
SELECT DISTINCT director 
FROM movies ORDER BY director ASC ;
```

```
SELECT title FROM movies
ORDER BY title ASC
LIMIT 5 OFFSET 5;
```

- When inserting data into a database, we need to use an INSERT statement, which declares which table to write into, the columns of data that we are filling, and one or more rows of data to insert. In general, each row of data you insert should contain values for every corresponding column in the table. You can insert multiple rows at a time by just listing them sequentially.

```
INSERT INTO mytable
VALUES (value_or_expr, another_value_or_expr, …),
       (value_or_expr_2, another_value_or_expr_2, …),
       …;
```
-  Whats is schema : I previously described a table in a database as a two-dimensional set of rows and columns, with the columns being the properties and the rows being instances of the entity in the table. In SQL, the database schema is what describes the structure of each table, and the datatypes that each column of the table can contain.


```
INSERT INTO movies VALUES (4, "Toy Story 4", "El Directore", 2015, 90);
```

```
INSERT INTO boxoffice VALUES (4, 8.7, 340000000, 270000000);
```

- TO update a row in the table use the UPDATE keyword

```
UPDATE movies
SET director = "John Lasseter"
WHERE id = 2;
```

```
UPDATE movies
SET year = 1999
WHERE id = 3;
```

```
UPDATE movies
SET title = "Toy Story 3", director = "Lee Unkrich"
WHERE id = 11;
```


- use the DELETE keyword

```
DELETE FROM movies
where year < 2005;
```

```
DELETE FROM movies
where director = "Andrew Stanton";
```


- When you have new entities and relationships to store in your database, you can create a new database table using the CREATE TABLE statement.

```
CREATE TABLE IF NOT EXISTS mytable (
    column DataType TableConstraint DEFAULT default_value,
    another_column DataType TableConstraint DEFAULT default_value,
    …
);
```

-Different databases support different data types, but the common types support numeric, string, and other miscellaneous things like dates, booleans, or even binary data


- An example schema for the Movies table that we've been using in the lesson up to now. 

```
CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER, 
    length_minutes INTEGER
);
```




