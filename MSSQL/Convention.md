> Always use store procedure for queries. Avoid writing inline SQL queries in the code.

1.  Provide DBA more information if problems happened.
2. Can cache result of SP to save resource.

> Always put `Set NOCOUNT On`. It can save lots of network traffic.

- 用來控制是否返回受 SQL 語句影響的行數的設置 (10 rows affected)

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

1. May cause performance issue.

> Avoid parameter sniffing 

 - Parameter sniffing 是指 SQL Server 在編譯存儲過程或參數化查詢時使用當前參數值來生成執行計劃。這個計劃會被緩存並用於後續的相同查詢。如果後續查詢的參數值分佈與最初的參數值不同，這個執行計劃可能並不適合，從而導致性能問題。

```SQL
Create Procedure dbo.xxx
	@Agentid bigint
As
Begin
If @Agentid = 'xxx'
Begin
	Exec dbo.ScanningStoredProcedure @Agentid
End

Else
Begin
	Exec dbo.SeekingStoredProcedure @Agentid
End
End
Go

/* seperate as two SP */
```

> Delete, update by batch

1. If delete more than 4,000 rows in same transaction, possible have table lock.
2. Avoid to have long running locks that caused other sessions being blocked.

> SARGable query (Search ARGument Able)

- Search optimization. Help improve search efficacy with index.

1. Indexes available

```SQL
if @roleid = 2
Begin
	Exec dbo.ScanningStoredProcedure
End
else if @roleid = 3
Begin
	Exec dbo.SeekingStoredProcedure
End
```

2. Where - like

```SQL
-- avoid
Select * From orders Where customerid like '%D'

-- Instead
Select * From orders Where customerid like 'D%'
```

3. Where calculation

```SQL
-- avoid 
Select id From t Where num/2=100

-- Instead 
Select id From t Where num = 100 * 2
```

> Avoid to use function or arithmetic at the left of equation in where condition.

This may lead Query Optimizer use index scan instead of index seek and cause performance issue.

```SQL
-- avoid 
Select id From t Where
Datediff(day, createdate, '2005-11-30')=0

-- Instead
Select id From t Where
createdate >= '2005-11-30' and
createdate < '2005-12-1'
```

>Avoid to use negative selection.

```SQL
NOT, !=, <>, !>, !<, NOT EXIST, NOT IN, NOT Like...
```

Using negative selection will cause Query Optimizer generate execution plan without using index seek.

> Avoid to use `Is Null` or `Is Not Null` in where condition.

1. suggest use `''` as default value.
2. Null will increase the complexity of SQL Server Storage Engine

> Avoid to have more than 50 lines in your Stored Procedure.

Having data logic inside SP, instead of business login in SP.
