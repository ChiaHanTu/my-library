###  非循環依賴原則 The Acyclic Dependencies Principle (ADP)

> 組件的依賴關係圖中不應存在循環依賴

#### 核心：
1. 依賴循環會導致耦合性增加
2. 變更傳染，一個模組的改動會連帶影響其他模組
3. 可能導致 build 與 release 出問題

#### 處理方式：
1. 中介者模式
2. 依賴反轉
3. 高階 -> 低階，低階依賴高階
4. 重構

### 穩定依賴原則 The Stable Dependencies Principle (SDP)

> 一個組件應該只依賴比自己更穩定的組件

穩定性評估：
1. Fan-in（扇入）：Incoming dependencies。有多少模組依賴該模組，指數越高越穩定
2. Fan-out（扇出）：Outgoing dependencies。該模組依賴多少模組，指數越低越穩定

#### 優點：
1. 降低維護成本
2. 增強穩定性
3. 提升測試性

### 穩定抽象原則  The Stable Abstractions Principle (SAP)

> 越穩定的模組應該越抽象（核心模組），越不穩定的模組應該越具體。

#### 優點：
1. 增強模組的靈活性與穩定性平衡
2. 降低維護成本
3. 促進程式碼複用


