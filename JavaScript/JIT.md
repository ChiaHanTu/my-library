> Just-In-Time Compilation，動態編譯，允許程式在執行時即時將高級語言轉換爲機器碼，以提升執行效率

## 工作流程

1. 解析 (Parsing)
   將 JS 程式碼解析成抽象語法樹(AST)
   
2. 基線編譯 (Baseline compilation)
   透過簡單快速的初步編譯來加速執行
   
3. 優化編譯 (Optimized Compilation)
   如果某段程式碼被多次執行(熱程式碼 Hot code)，JIT 會分析這段程式碼的模式並應用優化技術，如
   - 內聯函數（Inlining)：將頻繁執行的小函數直接插入主程式碼，提高效率
   - 常數折疊 (Constant Folding)：提前計算不變的值，例如 2+2 直接變成 4
   - 刪除死程式碼 (Dead Code Elimination)：去除不會執行的程式碼
