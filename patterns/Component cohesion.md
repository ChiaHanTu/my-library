### 複用/發布等價原則 The Reuse / Release Equivalence Principle (REP)

- 軟體模組的 **複用性** 和 **發布** 應當密切相關。
- 有效地重用建立在必須以獨立的、可發布的形式存在
- 模組必須可以獨立發佈，並防止影響依賴該模組的其他系統
#### 優勢：
1. 模組的蟲用
2. 降低變更風險

### 共同閉包原則 The Common Closure Principle (CCP)

-  一個組件中的類應當針對相同類型的變更一起封閉。
- 一個影響組件的變更應該僅影響該組件中的類，而不影響其他組件

#### 優勢：
1. 降低系統耦合度
2. 提升維護性

### The Common Reuse Principle (CRP)