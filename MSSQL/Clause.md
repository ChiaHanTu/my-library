## type IN

> type 表示資料庫物件的類型，IN 檢查物件類型為特定類型的物件

- 常見的物件類型代碼 
1. 'U' = User Table（使用者表格）
2. 'V' = View（視圖）
3. 'P' = Stored Procedure（預存程序）
4. 'FN' = Scalar Function（純量函數）
5. 'TF' = Table Function（表格函數）
6. 'TR' = Trigger（觸發器）

```sql
SELECT TOP 1 1 FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[TableName]') AND type IN (N'U')
```

- 檢查物件類型為使用者表格的物件

