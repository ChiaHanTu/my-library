
### 開放式系統互連模型 Open System Interconnection Model

> 應用層  Application layer

使用者真正與電腦溝通的點，扮演應用程式與下一層之間的介面。瀏覽器在必須處理遠端資源時，與應用層及其相關協定介接。負責辨識及確認可用的通訊夥伴，並驗證指定通訊類型是否能得到足夠的資源。

```
DHCP(v6), DNS, FTP, HTTP, SSH, RTP, GTP...
```

> 表現層（表示層）Presentation layer (deprecated)

將數據轉換為能與接收者的系統格式相容並適合傳輸的格式


> 會議層 Session layer (deprecated)

負責在數據傳輸中設定和維護電腦網路中兩台電腦之間的通訊連結


> 傳輸層 Transport layer

把傳輸表頭（TH）加至資料以形成封包。傳輸表頭包含了所使用的協定等傳送資訊。例如:傳輸控制協定（TCP）等。

```
TCP, TLS/SSL...
```

> 網路層 Network layer

決定數據的路徑選擇和轉寄，將網路表頭（NH）加至封包，以形成封包。網路表頭包含了網路資料。例如:網際網路協定（IP）等。

```
IP(v4, v6)...
```


> 資料連結層 Data Link layer

負責網路尋址、錯誤偵測和改錯。當表頭和表尾被加至封包時，會形成資訊框（Info Box）。數據鏈結串列頭（DLH）是包含了實體位址和錯誤偵測及改錯的方法。數據鏈結串列尾（DLT）是一串指示封包末端的字串。例如以太網、無線區域網路（Wi-Fi）和通用分組無線服務（GPRS）等。

