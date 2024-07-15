> Always use store procedure for queries. Avoid writing inline SQL queries in the code.

1.  Provide DBA more information if problems happened.
2. Can cache result of SP to save resource.

> Always put `Set NOCOUNT On`. It can save lots of network traffic.

```SQL
Set NOCOUNT On
Go
```

>Always use with (nolock) hint when select a table or view.

1. SQL server ignore table transactions lock status if you using a with (nolock) hint.
2. Locks in SQL server decrease and leads to performance increase.
3. Possible to read uncommitted data.

```SQL
Select a.Custid, a.UserName, a.Credit
From dbo.Customer with (nolock)
Where roleid = 1
```

> Avoid using `Select *` if possible, list the columns required.

1. Inefficiency in moving data to the consumer.
2. Binding Problems. Query Columns with same name will cause confused.

> Always specify table's column when invoked joining tables.

>Avoid use insert statement without specified columns to be inserted.

> Missing Go statement while define grant execute to stored procedure.

```SQL
Create Procedure [dbo].[Odin_Mgmt_Test]
As
Begin
	Set nocount on;
End
Go -- should add 
Grant execute on [dbo].[Odin+Mgmt_Test] to RoleOdin
```
> Avoid cross database to access data

1. Info security concern.
2. one database damage will cause others error.

> Avoid to use linked server

1. hard to troubleshoot.
2. Login may not be correct.

> Avoid to use Hint


