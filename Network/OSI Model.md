
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
TCP, TLS/SSL 
```