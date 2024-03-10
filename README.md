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

* Syntax
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

* Inserting Single row

* Example:

```sql
INSERT INTO Employees (FirstName, LastName, ManagerID, Salary, Designation, HireDate, DeptID) VALUES
('John', 'Doe', NULL, 60000.00, 'Software Engineer', '2015-03-01', 1);

```

## Select

