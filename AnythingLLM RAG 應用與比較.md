# AnythingLLM 與 RAG 應用  
## 全方位技術架構、企業部署與代理人系統深度研究報告

---

## 1. 執行摘要與戰略背景

在生成式人工智慧（Generative AI）從雲端 API 轉向地端部署（Local Deployment）的典範轉移中，
企業與開發者正面臨一個核心挑戰：如何將大型語言模型（LLM）的強大推理能力，
與組織內部的私有數據安全地結合，並在不依賴第三方 SaaS 服務的前提下，
實現數據主權（Data Sovereignty）。

AnythingLLM 是由 Mintplex Labs 開發的全端（Full-stack）應用程式，
不僅是聊天介面，更是一個整合：

- 檢索增強生成（RAG）
- 向量資料庫管理
- 多使用者權限控制
- AI 代理人（Agents）

的綜合系統。

---

## 2. AnythingLLM 的技術架構與部署範式

### 2.1 全端單體架構解析

**技術堆疊：JavaScript 生態系**

- **Frontend**
  - ViteJS + React
  - SPA 架構
  - Workspace 管理、聊天 UI

- **Server**
  - Node.js + Express
  - API、LLM 串接、身份驗證、權限控管

- **Collector**
  - Node.js
  - PDF / DOCX / Markdown 解析
  - Chunking 與文字清洗

- **Embed Widget**
  - 將聊天視窗嵌入外部網站
  - 適用於客服或公開知識庫

---

### 2.2 部署模式二元性

#### 2.2.1 AnythingLLM Desktop

- 內建 LanceDB（Serverless）
- 完全本機推理（Ollama / LM Studio）
- 資料完全不出機器
- 單一使用者（無 RBAC）

適合：
- 個人研究
- 高隱私需求
- POC

---

#### 2.2.2 AnythingLLM Docker（自託管）

- 多使用者系統（RBAC）
- RESTful API
- 可接外部向量資料庫（Pinecone / Qdrant / Weaviate）
- 支援 Chat Widget

| 功能 | Desktop | Docker |
|----|----|----|
| 使用者 | 單人 | 多人 |
| 向量 DB | 內建 LanceDB | LanceDB / 外部 |
| API | 本機 | 遠端 |
| RBAC | ❌ | ✅ |

---

## 3. LLM 與嵌入模型策略

### 3.1 LLM 分層設定

- **System LLM**
- **Workspace LLM**
- **Agent LLM**

可實現：
- 成本最佳化
- 不同場景不同模型

---

### 3.2 嵌入模型（Embedding）

- 系統級設定
- 更換需 Re-Embedding
- Desktop 內建離線 Embedder

---

## 4. RAG 管道核心機制

### 4.1 文件攝取與解析

- PDF / DOCX / TXT / MD / CSV
- Web Scraping（含登入）

限制：
- 複雜 PDF 建議搭配 Unstructured / LlamaParse

---

### 4.2 Chunking 策略

- Recursive Character Splitting
- Chunk Size：512–1024 Tokens
- Overlap：約 20%

---

### 4.3 檢索與重排序

1. 向量搜尋（Cosine Similarity）
2. Similarity Threshold
3. Reranking（Cross-Encoder）

---

### 4.4 Document Pinning

- 將全文直接注入 Prompt
- 適合：
  - 合約分析
  - 全文摘要
  - 翻譯

---

## 5. Agent 系統與技能

### 5.1 @agent 呼叫

- 專用 Agent LLM
- JSON Tool Calling

### 5.2 內建技能

- Web Browsing
- Web Scraping
- SQL Connector

---

## 6. 總結

AnythingLLM 是一個：
- 自託管
- 高度模組化
- RAG + Agent 一體化

的企業級 LLM 作業系統。
