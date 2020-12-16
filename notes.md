Java

Java Advance

Java Frameworks

Sql

Data Structures

Algorithms

Buid Tools

CICD

Testing

Production Environment

---

Database

We have a table named Employee with columns EmpId, EmpName, EmpDept, EmpSalary.

Write a sql statement to fetch records of all departments with number of employees in each department.

select empdept, count(empdept) as employees from Employees GROUP by empdept;

---

With Clause in Oracle

The SQL WITH clause was introduced by Oracle in the Oracle 9i release 2 database. The SQL WITH clause allows you to give a sub-query block a name (a process also called sub-query refactoring), which can be referenced in several places within the main SQL query.

The clause is used for defining a temporary relation such that the output of this temporary relation is available and is used by the query that is associated with the WITH clause.
Queries that have an associated WITH clause can also be written using nested sub-queries but doing so add more complexity to read/debug the SQL query.
WITH clause is not supported by all database system.
The name assigned to the sub-query is treated as though it was an inline view or table
The SQL WITH clause was introduced by Oracle in the Oracle 9i release 2 database.
Syntax:

WITH temporaryTable (averageValue) as
(SELECT avg(Attr1)
FROM Table),
SELECT Attr1
FROM Table
WHERE Table.Attr1 > temporaryTable.averageValue;

In this query, WITH clause is used to define a temporary relation temporaryTable that has only 1 attribute averageValue. averageValue holds the average value of column Attr1 described in relation Table. The SELECT statement that follows the WITH clause will produce only those tuples where the value of Attr1 in relation Table is greater than the average value obtained from the WITH clause statement.

Note: When a query with a WITH clause is executed, first the query mentioned within the clause is evaluated and the output of this evaluation is stored in a temporary relation. Following this, the main query associated with the WITH clause is finally executed that would use the temporary relation produced.

---

Objects in Databases

---

Temporary tables in sql

    gets deleted when current client session terminates

    a temporary table is only accessible to the connection that created that temporary table. It is not accessible to other connections. However, we can create temporary tables that are accessible to all the open connections. Such temporary tables are called global temporary tables. The name of the global temporary table starts with a double hash symbol (##).

    -local  #
        Local temporary tables

The names of these tables begin with #. The full length of this name must be shorter than 116 symbols. This type is more secure than “global,” as it is only available for the owning process. It is impossible to use them in views, and triggers won’t get associated with the Local temporary tables. When the session or procedure finishes, the Local temporary table is dropped.

    -global ##


        CREATE DATABASE schooldb

CREATE TABLE student
(
id INT PRIMARY KEY,
name VARCHAR(50) NOT NULL,
gender VARCHAR(50) NOT NULL,
age INT NOT NULL,
total_score INT NOT NULL,

)

INSERT INTO student

VALUES (1, 'Jolly', 'Female', 20, 500),
(2, 'Jon', 'Male', 22, 545),
(3, 'Sara', 'Female', 25, 600),
(4, 'Laura', 'Female', 18, 400),
(5, 'Alan', 'Male', 20, 500),
(6, 'Kate', 'Female', 22, 500),
(7, 'Joseph', 'Male', 18, 643),
(8, 'Mice', 'Male', 23, 543),
(9, 'Wise', 'Male', 21, 499),
(10, 'Elis', 'Female', 27, 400);

1. using SELECT INTO statement

USE schooldb;

SELECT name, age, gender
INTO #MaleStudents
FROM student
WHERE gender = 'Male'

2. using CREATE TABLE Command

USE schooldb;

CREATE TABLE #MaleStudents
(
name VARCHAR(50),
age int,
gender VARCHAR (50)

)

INSERT INTO #MaleStudents
SELECT name, age, gender
FROM student
WHERE gender = 'Male'

GLOBAL TEMPORARY TABLE

USE schooldb;

SELECT name, age, gender
INTO ##FemaleStudents
FROM student
WHERE gender = 'Female'

---

select distinct city from station where mod(id,2) = 0; oracle

    id % 2 = 0;         mysql
