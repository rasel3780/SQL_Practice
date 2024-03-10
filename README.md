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

* Example:

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
## Select


