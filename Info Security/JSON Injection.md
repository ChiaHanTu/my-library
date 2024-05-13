
> 攔截於客戶端與伺服端之間溝通的 JSON  格式資料，並藉此執行資料竊取或其他惡意程式

### Server-side 

> 可能導致 JSON Injection 的情境：

1.  伺服器以 JSON 格式儲存資料，並且包含帳號類型
2.  使用者名稱及密碼可以在不經過驗證、過濾即直接被存取
3.  使用簡單的串聯來創立 JSON string

 ```php
$json_string = '{
"accountType":"user",
"userName":"'.$_GET['userName'].'",
"pass":"'.$_GET['pass'].'"
}';
```

4.  惡意使用者附加數據到 input form 或是藉由 HTTP 標頭傳遞。此資料未經驗證而被發送到後端
5.  導致後端儲存類似如下的資料
   ```JSON
{ 
  "accountType":"user",
  "userName":"john",
  "accountType":"administrator",
  "pass":"password"
}
```
6.  當讀取這個資料時，授予了該 user 管理權，進而可能導致重要資料洩露、或是被執行惡意行為

### Client Side

> 可能導致 JSON Injection 的情境：

1.  如同上例一樣的 JSON string
2.  伺服端從未信任的來源且未經驗證取得包含惡意參數的 JSON 資料
3.  客戶端使用 `eval` 解析 JSON string
4.  
