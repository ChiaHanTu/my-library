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

## ID

```sql
(
	[ID] ASC
)
WITH (
    PAD_INDEX = OFF, -- 是否使索引頁面的填充程度用預設的填充因子
	STATISTICS_NORECOMPUTE = OFF, -- 是否自動更新統計資訊
	IGNORE_DUP_KEY = OFF, -- 是否忽略重複鍵值
	ALLOW_ROW_LOCKS = ON, -- 是否允許行層級的鎖定
	ALLOW_PAGE_LOCKS = ON -- 是否允許頁面層級的鎖定
)
ON [PRIMARY]
```
