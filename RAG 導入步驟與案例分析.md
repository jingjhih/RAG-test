# 企業級 RAG 技術導入  
## 導入路徑、架構優化與案例分析

---

## 1. RAG 的核心價值

RAG 解決：

- 幻覺（Hallucination）
- 知識截止
- 資料隱私

優於 Fine-tuning：

- 成本低
- 即時更新
- 可驗證來源

---

## 2. RAG 架構演進

### 2.1 Naive RAG

- Top-K 向量檢索
- 易受噪音影響

---

### 2.2 Advanced RAG

- Query Rewrite
- Hybrid Search
- Reranking

---

### 2.3 Modular RAG

- Routing
- 多檢索器

---

### 2.4 Agentic RAG（2025–2026）

- 自主檢索
- 多輪反思
- 成本與延遲較高

---

## 3. 導入六大階段

### 第一階段：資料準備

- SharePoint
- Google Drive
- Confluence
- DB / API

---

### 第二階段：Chunking

- Recursive
- Semantic
- Parent-Child

---

### 第三階段：Embedding

推薦：

- BGE-M3（中文）
- OpenAI text-embedding-3

---

### 第四階段：向量資料庫

| 類型 | 適用 |
|---|---|
| pgvector | 已有 PostgreSQL |
| LanceDB | 本地 |
| Pinecone | Serverless |

---

### 第五階段：檢索優化

- Hybrid Search
- Reranking
- Context Compression

---

### 第六階段：安全與權限

#### 三種模式：

1. Metadata Filtering
2. Post-Retrieval Filtering
3. Index Partitioning

---

## 4. 產業案例

- Morgan Stanley（金融）
- Notion（知識管理）
- Glean（企業搜尋）

---

## 5. 結論

> RAG 是企業 AI 的「長期正解」，  
> 而不是一次性的模型選擇。
