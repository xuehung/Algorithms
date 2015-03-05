## Basic Operation
- SELECT - extracts data from a database
```SQL
SELECT Names, Phones FROM Users;
SELECT * FROM Customers;
```
- UPDATE - updates data in a database
```SQL
UPDATE Users SET Name='Mike Cheng', City='Pittsburgh' WHERE Name='Hsueh-Hung Cheng';
```
- DELETE - deletes data from a database
```SQL
DELETE FROM Users WHERE Name='Mike Cheng';
```
- INSERT INTO - inserts new data into a database
```SQL
INSERT INTO Users (Name, City) VALUES ('Mike Cheng', 'Pittsburgh');
```


## Join
#### Inner Join
The INNER JOIN keyword selects all rows from both tables as long as there is a match between the columns in both tables
```SQL
SELECT column_name(s)
FROM table1
(INNER) JOIN table2
ON table1.column_name=table2.column_name;
```

#### Left Join
The LEFT JOIN keyword returns all rows from the left table (table1), with the matching rows in the right table (table2). The result is NULL in the right side when there is no match.
```SQL
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name=table2.column_name;
```

#### Right Join
The RIGHT JOIN keyword returns all rows from the right table (table2), with the matching rows in the left table (table1). The result is NULL in the left side when there is no match.
```SQL
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name=table2.column_name;
```
