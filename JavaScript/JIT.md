> Just-In-Time Compilation，動態編譯，允許程式在執行時即時將高級語言轉換爲機器碼，以提升執行效率

## 工作流程

1. 解析 (Parsing)
   將 JS 程式碼解析成抽象語法樹(AST)
   
2. 基線編譯 (Baseline compilation)
   透過簡單快速的初步編譯來加速執行
   
3. 優化編譯 (Optimized Compilation)