
> 攔截於客戶端與伺服端之間溝通的 JSON  格式資料，並藉此執行資料竊取或其他惡意程式

### Server-side 

> 可能導致 JSON Injection 的情境：

1. 伺服器以 JSON 格式儲存資料，並且包含帳號類型
2. 使用者名稱及密碼可以在不經過驗證、過濾即直接被存取
3. 使用簡單的串聯來創立 JSON string

 ```php
$json_string = '{
"accountType":"user",
"userName":"'.$_GET['userName'].'",
"pass":"'.$_GET['pass'].'"
}';
```

4.  惡意使用者附加數據到 input form HTTP 標頭傳遞的使用者名。此資料未經審查後端被發送到後端