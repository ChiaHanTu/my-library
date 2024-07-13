### DBMS Database Management Studio

- Relational: MSSQL Server, MySQL, Oracle
- None Relational: NoSQL
### SSMS SQL Server Management Studio 

---
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

--- 
- database

```SQL
Create database TEST2
Alter database TEST3 modify name=TEST1
Drop database TEST2
/* if other connection is still exist. It cannot drop database*/
```

- table 

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

- Create constraints
  
```SQL
Create Table tableEmployees(
	EmployeeId int Primary Key Not Null, /* Primary key */
	EmplyeeName varchar(50) Not Null, /* Not Null */
	Phone int Not Null Unique, /* Unique */
	DepID int Foreign key references
	tableDeparments(DepID) Not Null, /* Foreign key*/
	Salary Decimal (10, 2) Default 3000.00 /* Default */
	Age int Not Null Check (Age >= 18) /* Check */ 
)

Create Table tableDeparments(
	DepID int primary key Not Null,
	DepartmentName varchar(50) Not Null
)
```

- Alter Constraint

```SQL
/* Alter table unique key */
Alter Table tableEmployees
Add Constraint U_Phone
Unique(Phone)

/* Add check */
Alter Table tableEmployees
Add Constraint CHK_EmployeeAge
Check(Age >= 18)

/* Drop check */
Alter Table tableEmployees
Drop Constraint CHK_EmployeeAge
```
### Data manipulation

```SQL
/* Insert */
Insert Into tableEmployees
(EmployeeID, EmployeeName, Phone, DepID)
Values(1005, 'Steve', 44889988, 1)

/* Same result*/
Insert Into tableEmployees
Values(1005, 'Steve', 44889988, 1)
```

```SQL
/* Update */
Update tableEmployees
Set EmployeeName='Frank', Phone=56875599
Where EmployeeID=1001
```

```SQL
/* All data will be deleted*/
Delete tableEmployees

/* Delete */
Delete tableEmployees
Where EmployeeID=1001
```

### Logical Operations

```SQL
/* between */
Select *
From Person.Person
Where BusinessEntityID between 1 and 5

/* In */
Select *
From Person.Person
Where BusinessEntityID In(1,2,5)
```

### Sorting and grouping data

```SQL
/* Distinct */
Select Distinct PersonType
From Person.Person

/* Order by */
Select FirstName, MiddleName, LastName
From Person.Person Order By FirstName ASC /* or DESC */

/* Group by */
Select Shelf, sum(Quantity)
From Production.ProductInventory
Group By Shelf
Order By Shelf

/* Having */
Select Shelf, sum(Quantity)
From Production.ProductInventory
Group By Shelf Having Shelf='A'

/* same result */
Select Shelf, sum(Quantity)
From Production.ProductInventory
Where Shelf='A'
Group By Shelf

/* Where clause should process right after From clause
and process before Group By Clause */

/* Having Clause is executed after Group By */

/* Aggregate */
Select Shelf, sum(Quantity) As Quantity,
From Production.ProductInventory
Group By Shelf Having sum(Quantity)>10000 Order By Shelf

/* If filtering can be done without the aggregate function.
Then must use Where clause because it improves performance */
```

### Wildcard operation with Like / Not Like

```SQL
/* Find data which starts with ang */
Select * From Person.Person Where FirstName Like 'ang%'

/* Find data which ends with a */
Select * From Person.Person Where FirstName Like '%a'

/* Find data which contains inda */
Select * From Person.Person Where FirstName Like '%inda%'
```

```SQL
/* Find six letter names endsing with inda */
Select * From Person.Person Where FirstName Like '__inda'
```

```SQL
/* Find first names starts with a, b or c */
Select * From Person.Person Where FirstName Like '[abc]%'

/* Same result */
Select * From Person.Person Where FirstName Like '[a-c]%'
```

### Case function 

```SQL
Select DepID, DepartmentName,
	Case DepartmentName
		When 'IT' Then 'Information Technology'
		When 'HR' Then 'Human Resources'
		Else 'Financial Institution'
	END As 'Department Long Name'
from tableDepartments
```

### Conversion function 

```SQL
/* Transform Date type to string type */
Select FirstName, LastName, ModifiedDate,
	Case(ModifiedDate as varchar) DateToText
From Person.Person
```
