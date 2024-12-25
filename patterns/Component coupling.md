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
1. Fan-in：有多少魔ㄗㄨ