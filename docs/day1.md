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

##### Data Definition Language (DDL) 
This component of the SQL language is used to create and modify tables and other objects in the database. For tables there are three main commands:

CREATE TABLE tablename to create a table in the database 

DROP TABLE tablename to remove a table from the database

ALTER TABLE tablename to add or remove columns from a table in the database

##### Data Manipulation Language (DML) 
This component of the SQL language is used to manipulate data within a table. There are four main commands:

SELECT to select rows of data from a table

INSERT to insert rows of data into a table

UPDATE to change rows of data in a table

DELETE to remove rows of data from a table

##### The Data Control Language (DCL) 
This component of the SQL language is used to create privileges to allow users access to, and manipulation of, the database. There are two main commands:

GRANT to grant a privilege to a user

REVOKE to revoke (remove) a privilege from a user


#### Demo
[Hello world demo!](https://github.com/ffliza/training/blob/master/Activity-1-1.ipynb)

[Create a database]()

[How to get help? Check the documentation on Create database.](https://dev.mysql.com/doc/refman/8.0/en/create-database.html)


## Session 2

### Data Manipulation Language --- single table SELECT statements
```sql
select * from Table_A;
```
