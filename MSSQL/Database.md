### DBMS Database Management Studio

- Relational: MSSQL Server, MySQL, Oracle
- None Relational: NoSQL
### SSMS SQL Server Management Studio 

## Normalization

- Organizing data in the database.
- Eliminating redundant data.
- Ensuring data dependencies make sense.

> Normalization guidelines are divided into normal forms. As the format or the way a database structure is laid out.
### 1NF (First Normal Form)

 - The data in each column should only have single value.
 - Each set of related data should be identified with a primary key.
 - All the columns in a table should have unique names.
### 2NF

- Include all the rules of the 1NF
- Each set of related data should be stored in a separate table.
### 3NF

-  Include all the rules of the 2NF.
- The table shouldn't contain columns that are not fully depend upon primary key.

```SQL
Create database TEST2
Alter database TEST3 modify name=TEST1
Drop database TEST2
/* if other connection is still exist. It cannot drop database*/
```

```SQL
Use Company /* Selected Database */
Go
/* Create */
Create Table tableEmployees(
	EmployeeId int primary key Not Null,
	EmplyeeName varchar(50) Not Null,
	Phone int Not Null,
	DepID int Not Null,
)

/* Rename */
EXEC sp_rename 'tableEmployees', 'Employees'

/* Drop */
Drop Table Employees
```

## Constraints

```SQL
Create Table tableEmployees(
	EmployeeId int primary key Not Null, /* Primary key */
	EmplyeeName varchar(50) Not Null, /* Not Null */
	Phone int Not Null,
	DepID int Not Null,
	Salary Decimal (10, 2) Default 3000.00 /* Default */
)
```




