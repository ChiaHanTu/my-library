
# On-Prem & Beyond：大語言模型時代的 AI 安全防禦藍圖 - 徐方繹(Fngi)

- Twinkle AI 繁中 Base AI

## 雲端

- AI Prompt 攻擊
- 資料外洩：Google Cloud DLP 偵測敏感性資料，like firewall on cloud
- 雲端防護：GCP Armor

## 地端

- 沙箱：避免資料污染
- 隔離：權限控管
- 稽核

## OWASP LLM Security

Top 10 Attack 繁中: https://edward-playground.github.io/top10-showcase/


## OWASP API Securuty 

---
# API 的新護照：從 REST 到 MCP 的入境指南 - 雷幃程

## Agent 

1. System prompt: 策略層，說明什麼情境下呼叫對應的 Tool
2. Description：功能層，說明呼叫 Tool 時的注意事項



- Arguments (依照 Workflow 設計)
- Filter

## MCP 分層

--- 
## 私有化的速度與安全：用OpenAI 開源權重 GPT-OSS 模型實踐 AI Agent - Ian


## 開源 LLM 模型：

- **GPT-OSS**, Meta LLaMA 3, Qwen 2.5
### 考量

- 效能
- 維護成本
- 內部控管與審核機制

### 測試情境

- 是否能了解使用者意圖 -> 語意理解
- Function call 成功率
- 由另一個 AI 作為評判員，從不同面向評測模型回答品質
- 評估機制：
	- 測試設計：一般問答（不含 Function Calling）
	- 模型扮演 Office AI Agent
	- 採用 50 個辦公室日常問題
	- 知識庫內容預埋在 system prompt
- 多維度評分、每題最高 6 分，核心指標各 2 分、一般指標各 1 分）
- 核心指標：
	- 依據性：是否完全依據知識集、無虛構內容
	- 拒答正確性 - 對知識集外問題能否正確拒答
- 一般指標：
	- 完整度：是否完整回答所有紫問題
	- 清晰度：問答結構與語句是否清楚易懂

## 測試情境

- 對 AI Agent 對多工具選擇能力
- 核心評估機制：
	- 完全正確
	- 部分正確
	- 錯誤
	- 不需工具
- 








