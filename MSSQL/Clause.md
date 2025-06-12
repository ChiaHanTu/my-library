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
    PAD_INDEX = OFF, -- 控制索引頁面的填充程度，OFF 表示使用預設的填充因子
	STATISTICS_NORECOMPUTE = OFF,
	IGNORE_DUP_KEY = OFF,
	ALLOW_ROW_LOCKS = ON,
	ALLOW_PAGE_LOCKS = ON
)
ON [PRIMARY]
```

###PAD_INDEX = OFF：
- 



- STATISTICS_NORECOMPUTE = OFF：

- 控制是否自動更新統計資訊

- OFF 表示允許自動更新統計資訊

- IGNORE_DUP_KEY = OFF：

- 控制重複鍵值的處理方式

- OFF 表示不忽略重複鍵值，會產生錯誤

- ALLOW_ROW_LOCKS = ON：

- 允許行層級的鎖定

- ON 表示可以使用行鎖定

- ALLOW_PAGE_LOCKS = ON：

- 允許頁面層級的鎖定

- ON 表示可以使用頁面鎖定