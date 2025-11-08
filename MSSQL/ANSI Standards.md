## SET ANSI_NULLS ON;

> ANSI 標準設定，控制如何處理 NULL 值的比較和運算。

```sql
-- 以下比較都會返回 UNKNOWN（在 WHERE 子句中視為 FALSE）
SELECT * FROM users WHERE name = NULL; -- 返回 0 筆記錄
SELECT * FROM users WHERE name <> NULL; -- 返回 0 筆記錄
SELECT * FROM users WHERE NULL = NULL; -- 返回 0 筆記錄

-- 正確的 NULL 檢查方式
SELECT * FROM users WHERE name IS NULL; -- 正確
SELECT * FROM users WHERE name IS NOT NULL; -- 正確
```

## SET ANSI_PADDING ON;

> 控制 SQL Server 如何處理字符和二進制數據類型中的尾隨空格

**當 ANSI_PADDING 設為 ON 時：**

- `char` 和 `binary` 類型會保留尾隨空格
- `varchar` 和 `varbinary` 類型會移除尾隨空格
- 這是 SQL Server 的預設行為，也符合 ANSI SQL 標準

**當 ANSI_PADDING 設為 OFF 時：**

- 所有字符和二進制類型都會移除尾隨空格
- 這可能導致數據截斷或不一致的行為