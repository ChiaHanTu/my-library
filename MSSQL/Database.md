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
		Cast(ModifiedDate as varchar) DateToText
From Person.Person

/* Same result */
Select FirstName, LastName, ModifiedDate,
		Convert(varchar(11), ModifiedDate) DateToText
From Person.Person

/* 2009-01-07 00:00:00.000 -> Jan 7 2009 12:00 AM */
```

![[Pasted image 20240713221612.png]]
### Inner Join (交集)

```SQL
/* Join / Inner join. Join two table data with same DepID */
Select EmployeeID, EmployeeName, DepartmentName
From tableEmployees
Join tableDepartments
On tableEmployees.DepID=tableDepartments.DepID
```

### Left Join / Right Join (左交集/右交集)

```SQL
/* Left(outer) / Right(outer) Join.
Pick all data from left table and data from right table with same ProductID,
it will show S.SalesOrderDetailID from left if it contains, or will display null */
Select Name, SalesOrderDetailID
From Production.Product as P
Left Join Sales.SalesOrderDetail as S
On P.ProductID=S.ProductID
```
### Full Join (聯集)

```SQL
/* Full(outer) Join.
Pick all data from left and right table with same ProductID, */
Select Name, SalesOrderDetailID
From Production.Product as P
Full Join Sales.SalesOrderDetail as S
On P.ProductID=S.ProductID
```
### Self Join

```SQL
/* Finds Product with the same list price */
Select P1.Name, P2 Name, P1 ListPrice
From Production.Product P1
Join Production.Product P2
On P1.ListPrice = P2.ListPrice
	And P1.ListPrice <> 0 -- Exclude products with no price
	And P1.Name <> P2.Name -- Exclude the same product
Order By ListPrice

/* Same result */
Select P1.Name, P2 Name, P1 ListPrice
From Production.Product as P1, Production.Product as P2
Where P1.ListPrice = P2.ListPrice
	And P1.ListPrice <> 0 -- value is not equal to 0 
	And P1.Name <> P2.Name
```

## Set Operation

- The result sets of all queries must have the same number of columns.
- In every result set the data type of each column must match the data type of its corresponding column in the first result set.
### Union / Union All

```SQL
/* Union, get distinct values */
Select CurrencyCode -- 109
from Sales.CountryRegionCurrency
Union
Select CurrencyCode --105
from Sales.Currency
/* The result is 105 because some duplicate values */

/* Union All, including duplicate values*/
Select CurrencyCode -- 109
from Sales.CountryRegionCurrency
Union All
Select CurrencyCode --105
from Sales.Currency
/* The result is 214 */
```
### Intersect 

```SQL
Select JobTitle
From HumanResources.Employee
Where Gender = 'M' -- 206
Intersect -- 26
Select JobTitle
From HumanResources.Employee
Where Gender = 'F' -- 84

/* Same result */
Select Distinct JobTitle
From HumanResources.Employee As EM
Join HumanResources.Employee As EF
On EM.JobTitle = EF.JobTitle
	And EM.Gender = 'M'
	And EF.Gender = 'F'
```

### Except

```SQL
/* Jobtitle just held by male */
Select JobTitle
From HumanResources.Employee
Where Gender = 'M' -- 206
Except -- 31
Select JobTitle
From HumanResources.Employee
Where Gender = 'F' -- 84
```

## Subqueries

```SQL
/* Return the count of certain product with specific ID */
Select Count(*) From Sales.SalesOrderDetail
Where ProductID = (
	Select ProductID
	From Production.Product
	Where Name = 'Blade'
)

/* Select products that are not ordered yet */
Select * From Production.Product as P
Where Not Exist
	(Select ProductID from Sales.SalesOrderDetail as S
	Where P.ProductID = S.ProductID)


/* Put data into another table */
Insert Into Person.StateProvinceTest
	Select StatusProvinceCode,
			CountryRegionCode,
			IsOnlyStateProvinceFlag,
			Name,
			TerritoryID,
			ModifiedDate
	From Person.StateProvince

/* Change all Canada's territoryID into 99 */
Update Person.StateProvinceTest
Set TerritoryID = 99
Where CountryCode In
	(Select CountryRegionCode from Person.StateProvince
	Where CountryRegionCode = 'CA')

/* Delete all Canada data */
Delete From Person.StateProvinceTest
Where CountryCode In
	(Select CountryRegionCode from Person.StateProvince
	Where CountryRegionCode = 'CA')
```

## Datetime function 

```SQL
Select DATEPART(YEAR, '2020-01-23') -- 2020
```





