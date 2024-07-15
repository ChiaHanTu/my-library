
> Always Create a Stored Procedure as 

```SQL
[dbo].[{ProjectName}_{ProductShortName}_{ModuleName}_{FunctionName}_{VersionNo}]
```

> Always create a view with a prefix v follow by Pascal Casing

```SQL
Create View [dbo].[vAgentBalance]
```

> Always create a function with a prefix f follow by Pascal Casing

```SQL
Create Function [dbo].[fGetPTGroupType]
```

> Table, SP, Function, View, Column name

- Use Pascal Casing.

> Variables for SP

- Use Camel Casing for input/output parameters and variable for SP.
