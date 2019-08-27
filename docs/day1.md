# Introduction to SQL

## Session 1

### Key Components of SQL server

1. Database Engine: This part of SQL Server actually creates and drives relational databases.

2. SQL Server Analysis Services (SSAS): SSAS is the data-analysis component of SQL Server. It can create OLAP (OnLine Analytical Processing) cubes — sophisticated programming objects for organizing data inside a relational database — and do data mining (pulling relevant data out of a database in response to an ad-hoc question).

3. SQL Server Reporting Services (SSRS): SSRS is a component of SQL Server that provides reporting regardless of a database’s operating system.

4. SQL Server Integration Services (SSIS): SSIS is a component of SQL Server that does the Extract, Transform, and Load (ETL) process that cleans up and formats raw data from source systems for inclusion in the database as ready-to-use information.


### SQL consists of three components:

1. Data Definition Language (DDL)
2. Data Manipulation Language (DML)
3. Data Control Language (DCL)

#### Data Definition Language (DDL) 
This component of the SQL language is used to create and modify tables and other objects in the database. For tables there are three main commands:

CREATE TABLE tablename to create a table in the database 

DROP TABLE tablename to remove a table from the database

ALTER TABLE tablename to add or remove columns from a table in the database

#### Data Manipulation Language (DML) 
This component of the SQL language is used to manipulate data within a table. There are four main commands:

SELECT to select rows of data from a table

INSERT to insert rows of data into a table

UPDATE to change rows of data in a table

DELETE to remove rows of data from a table

#### The Data Control Language (DCL) 
This component of the SQL language is used to create privileges to allow users access to, and manipulation of, the database. There are two main commands:

GRANT to grant a privilege to a user

REVOKE to revoke (remove) a privilege from a user


#### Demo
[Hello world demo!](https://github.com/ffliza/training/blob/master/Activity-1-1.ipynb)

[Create a database]()

[How to get help? Check the documentation on Create database.](https://dev.mysql.com/doc/refman/8.0/en/create-database.html)


## Session 2

### Data Types: int

```sql
create table tb_test_int_type(
    int_10 int(10),
    int_10_with_zf int(10) zerofill,
    unit int unsigned
);
```

```sql
insert into tb_test_int_type(int_10, int_10_with_zf, unit)
values (123456, 123456,3147483647), (123456, 4294967291,3147483647);
```

```sql
select * from tb_test_int_type; 

# int_10, int_10_with_zf, unit
'123456', '0000123456', '3147483647'
'123456', '4294967291', '3147483647'
```
### Data Types: float



## Session 3

### Data Manipulation Language --- single table SELECT statements
```sql
select * from Table_A;
```


### Joins


```
Table 1 − Staff Table is as follows.

+----+----------+-----+-----------+----------+
| ID | NAME     | AGE | ADDRESS   | SALARY   |
+----+----------+-----+-----------+----------+
|  1 | Joe      |  32 | London    |  2000.00 |
|  2 | Mark     |  25 | Colchester|  1500.00 |
|  3 | Daniel   |  23 | Chelsmford|  2000.00 |
|  4 | Linda    |  25 | Cambridge |  6500.00 |
|  5 | Adam     |  27 | Liverpool |  3500.00 |
|  6 | Jasmine  |  22 | Manchester|  5500.00 |
|  7 | Paul     |  24 | London    |  7000.00 |
+----+----------+-----+-----------+----------+
```

```
 Table 2 - HOLIDAYS is as follows.
+-----+---------------------+-------------+-------------+
| OID | APPROVAL_DATE       | Staff_ID    | DAYS_BOOKED |
+-----+---------------------+-------------+-------------+
| 102 | 2009-10-08 00:00:00 |           3 |   5         |
| 100 | 2009-10-12 00:00:00 |           3 |   9         |
| 101 | 2009-11-20 00:00:00 |           1 |   3         |
| 103 | 2008-05-20 00:00:00 |           7 |   12        |
+-----+---------------------+-------------+-------------+

```
## INNER JOIN
Basic Syntax: 

```sql
SELECT table1.column1, table2.column2...
FROM table1
INNER JOIN table2
ON table1.common_field = table2.common_field;
```

Now, let us join these two tables using the INNER JOIN as follows 

```sql

   SELECT  ID, NAME, DAYS_BOOKED, APPROVAL_DATE
   FROM STAFF
   INNER JOIN HOLIDAYS
   ON STAFF.ID = HOLIDAYS.STAFF_ID;

```
Output: 

```
+----+----------+---------------+---------------------+
| ID | NAME     | DAYS_BOOKED   | APPROVAL_DATE       |
+----+----------+---------------+---------------------+
|  3 | Daniel   |   5           | 2009-10-08 00:00:00 |
|  3 | Daniel   |   9           | 2009-10-12 00:00:00 |
|  1 | Joe      |   3           | 2009-11-20 00:00:00 |
|  7 | Paul     |   12          | 2008-05-20 00:00:00 |
+----+----------+---------------+---------------------+

```

## LEFT JOIN

The basic syntax of a LEFT JOIN is as follows.

```sql
SELECT table1.column1, table2.column2...
FROM table1
LEFT JOIN table2
ON table1.common_field = table2.common_field;
```

Now, let us join tables 1 and 2 using the LEFT JOIN as follows 

```1sql 
  SELECT  ID, NAME, DAYS_BOOKED, APPROVAL_DATE
   FROM STAFF
   LEFT JOIN HOLIDAYS
   ON STAFF.ID = HOLIDAYS.STAFF_ID;
 ```
Output: 
 
```
+----+----------+---------------+---------------------+
| ID | NAME     | DAYS_BOOKED   | APPROVAL_DATE       |
+----+----------+---------------+---------------------+
|  1 | Joe      | 3             | 2009-11-20 00:00:00 |
|  2 | Mark     | NULL          | NULL                |
|  3 | Daniel   | 5             | 2009-10-08 00:00:00 |
|  3 | Daniel   | 9             | 2009-10-12 00:00:00 |
|  4 | Linda    | NULL          | NULL                |
|  5 | Adam     | NULL          | NULL                |
|  6 | Jasmine  | NULL          | NULL                |
|  7 | Paul     | 12            | 2008-05-20 00:00:00 |
+----+----------+---------------+---------------------+
```


## RIGHT JOIN

The basic syntax of a RIGHT JOIN is as follows.

```sql
SELECT table1.column1, table2.column2...
FROM table1
RIGHT JOIN table2
ON table1.common_field = table2.common_field;
```

Now, let us join tables 1 and 2 using the RIGHT JOIN as follows 

```1sql 
  SELECT  ID, NAME, DAYS_BOOKED, APPROVAL_DATE, ADDRESS
   FROM STAFF
   RIGHT JOIN HOLIDAYS
   ON STAFF.ID = HOLIDAYS.STAFF_ID;
 ```
Output: 

```
+----+----------+---------------+---------------------+-------------+
| ID | NAME     | DAYS_BOOKED   | APPROVAL_DATE       | ADDRESS     |
+----+----------+---------------+---------------------+-------------+
|  3 | Daniel   |   5           | 2009-10-08 00:00:00 | Chelsmford  |
|  3 | Daniel   |   9           | 2009-10-12 00:00:00 | Chelsmford  |
|  1 | Joe      |   3           | 2009-11-20 00:00:00 | London      |
|  7 | Paul     |   12          | 2008-05-20 00:00:00 | London      |
+----+----------+---------------+---------------------+-------------+
```


## Create Table

Example

### Create Prisoners Table
```sql
CREATE TABLE Prisoners(
    PrisonersID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255) 
);
```
### select Prisoners table 

```sql
SELECT * FROM Prisoners
```
Output: empty table

```
+-------------+-----------+------------+---------+------+
| PrisonersID | LastName  | FirstName  | Address | City |
+-------------+-----------+------------+---------+------+
```

### Insert data into Prisoners table 

```sql

INSERT INTO Prisoners (LastName, FirstName, Address, City) 
VALUES ('Doe','John','21 X street','London');

```
### select Prisoners table 

```sql
SELECT * FROM Prisoners
```
Output:

```
+-------------+-----------+------------+-------------+--------+
| PrisonersID | LastName  | FirstName  | Address     | City   |
+-------------+-----------+------------+-------------+--------+
| 1	          | Doe       | John       | 21 X street | London |
+-------------+-----------+------------+-------------+--------+
```
