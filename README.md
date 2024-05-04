# SQL_Practice

## Database Creation

```sql
CREATE DATABASE DatabaseName

```
## Table Creation

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

* Example

```sql
CREATE TABLE Employees(
	EmpID INT NOT NULL IDENTITY(1,1) PRIMARY KEY,
	FirstName NVARCHAR(100),
	LastName NVARCHAR(100),
	ManagerID INT NULL,
	Salary DECIMAL(10,2) NOT NULL,
	Designation NVARCHAR(100),
	HireDate DATE NOT NULL,
	DeptID INT NOT NULL
);
```
## Insert

* Syntax: <br>
INSERT INTO table_name (column1, column2, column3, ...) <br>
VALUES (value1, value2, value3, ...);

* Inserting Single row

```sql
INSERT INTO Employees (FirstName, LastName, ManagerID, Salary, Designation, HireDate, DeptID) VALUES
('John', 'Doe', NULL, 60000.00, 'Software Engineer', '2015-03-01', 1);

```

* Inserting Multiple Rows:
```sql
INSERT INTO Employees(FirstName, LastName, ManagerID, Salary, Designation, HireDate, DeptID) VALUES
    ('Fatima', 'Akhtar', 1, 45000.00, 'Software Developer', '2023-02-15', 2),
    ('Ahmed', 'Khan', 1, 55000.00, 'Project Manager', '2022-12-10', 3),
    ('Aisha', 'Begum', 3, 60000.00, 'Senior Developer', '2023-03-20', 1),
    ('Abdul', 'Ali', 3, 65000.00, 'Team Lead', '2023-04-05', 2);
```

## Updating Data
* UPDATE Syntax: <br>
UPDATE table_name <br>
SET column1 = value1, column2 = value2, ... <br>
WHERE condition;

```sql
UPDATE Employees
SET FirstName='Mohammad', LastName='Rahman'
WHERE EmpID=1;
```

## ORDER BY

* BY Default ORDER BY sort result in ascending order

```sql
SELECT * FROM Employees
ORDER BY Salary;

SELECT * FROM Employees
ORDER BY HireDate ASC
```
* To sort the result in descending order use `DESC` Keyword
```sql
SELECT * FROM Employees
ORDER BY Salary DESC;
```



## LIKE 

* used in a WHERE clause to search for a specified pattern in a column.

* The percent sign % represents zero, one, or multiple characters
* The underscore sign _ represents one, single character

* Return All Employee that FirstName Start With 'a'

```SQL
SELECT * FROM Employees
WHERE FirstName LIKE 'a%';
```

* Return All Employee that FirstName End With 'a'

```SQL
SELECT * FROM Employees
WHERE FirstName LIKE '%a';
```

* Return All Employee that FirstName Start With 'a' and End With 'a'

```SQL
SELECT * FROM Employees
WHERE FirstName LIKE 'a%a';
```
* Return All Employee that FirstName contains 'a'

```SQL
SELECT * FROM Employees
WHERE FirstName LIKE '%a%';
```

## TOP

* specify the number of records to return
* is useful on large tables with thousands of records. Returning a large number of records can impact performance.
* Not all database systems support the SELECT TOP clause. MySQL supports the LIMIT clause to select a limited number of records, while Oracle uses FETCH FIRST n ROWS ONLY and ROWNUM.

```SQL
SELECT TOP 3 * FROM Employees;
```

```SQL
SELECT TOP 3 * FROM Employees
ORDER BY FirstName;
```

```SQL
SELECT TOP 3 * FROM Employees
ORDER BY Salary DESC;
```

```SQL
SELECT TOP 5 * FROM Employees
WHERE ManagerID=3;
```

## Aggregate function

* An aggregate function is a function that performs a calculation on a set of values, and returns a single value.
* The GROUP BY clause splits the result-set into groups of values and the aggregate function can be used to return a single value for each group.

* The most commonly used SQL aggregate functions are:

<ul>
  <li>MIN() - returns the smallest value within the selected column</li>
  <li>MAX() - returns the largest value within the selected column</li>
  <li>COUNT() - returns the number of rows in a set</li>
  <li>SUM() - returns the total sum of a numerical column</li>
  <li>AVG() - returns the average value of a numerical column</li>
</ul>

### MIN () and MAX() Function

* The MIN() function returns the smallest value of the selected column.

```SQL
  SELECT MIN(Salary)
  FROM Employees;
```
* The MAX() function returns the largest value of the selected column.

```SQL
  SELECT MAX(Salary)
  FROM Employees;
```

* When you use MIN() or MAX(), the returned column will not have a descriptive name. To give the column a descriptive name, use the AS keyword

```SQL
  SELECT MIN(Salary) as LowestSalary
  FROM Employees;
```

### COUNT 
* The COUNT() function returns the number of rows that matches a specified criterion.
* COUNT() Function take exactly 1 argument


Find the total number of rows in the Employees table:

```SQL
SELECT COUNT(*)  FROM Employees ;
```

* If you specify a column name instead of (*), NULL values will not be counted.
```SQL
SELECT COUNT(ManagerID) as ManagerId FROM Employees ;
```

* You can add a WHERE clause to specify conditions:

```SQL
SELECT COUNT(FirstName) 
FROM Employees WHERE Salary<50000;
```
## SUM() 
* The SUM() function returns the total sum of a numeric column.

```SQL

  SELECT SUM(Salary)
  FROM Employees;
```

```SQL
  SELECT SUM(Salary)
  FROM Employees 
  WHERE Designation='Project Manager';

```

```SQL

  SELECT DeptID, SUM(Salary) AS [Total Salary]
  FROM Employees
  GROUP BY DeptID; 

```

```SQL

  SELECT DeptID, SUM(Salary) as monthly, SUM(Salary*1.5) as bonus 
  FROM Employees
  GROUP BY DeptID;

```

# AVG()
* The AVG() function returns the average value of a numeric column.


```SQL
  SELECT AVG(Salary)
  FROM Employees;
```

```SQL
  SELECT DeptID, AVG(Salary)
  FROM Employees
  GROUP BY DeptID;
```

```SQL
  SELECT EmpID, FirstName, Salary
  FROM Employees
  WHERE Salary> (SELECT AVG(Salary) FROM Employees); 
```

## BETWEEN 

* The BETWEEN operator selects values within a given range. 
* The values can be numbers, text, or dates.
* The BETWEEN operator is inclusive: begin and end values are included. 

```SQL
SELECT * FROM Employees 
WHERE Salary BETWEEN 30000 AND 50000;

```

```SQL

SELECT * FROM Employees 
WHERE Salary NOT BETWEEN 30000 AND 50000;
```

## INNER JOIN 

* JOIN and INNER JOIN will return the same result.
* INNER is the default join type for JOIN
```SQL
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```