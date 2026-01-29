# RAG 資料前處理實作流程與工具推薦

---

## 1. 執行摘要

在 RAG 架構中，模型不是瓶頸，
**資料品質與檢索精度才是關鍵**。

核心觀念：
> Garbage In, Garbage Out（在向量空間中被放大）

---

## 2. 理論框架與核心挑戰

### 2.1 語意稀釋問題（Semantic Dilution）

- 頁眉、頁腳、亂碼
- 切斷的句子
- 會導致向量偏移

---

### 2.2 從非結構化到語意結構化

三層還原：

1. 版面結構（Layout）
2. 邏輯結構（Heading / Table）
3. 語意關聯（Metadata）

---

### 2.3 標準前處理 Pipeline

1. Ingestion & Parsing  
2. Cleaning & Normalization  
3. Semantic Chunking  
4. Metadata Extraction  
5. Embedding & Indexing  

---

## 3. 文件解析工具比較

### 3.1 LlamaParse

- 表格 → Markdown
- 多模態理解
- SaaS（需上傳）

---

### 3.2 Unstructured.io

- 開源
- Docker / On-prem
- 支援格式最多

---

### 3.3 Docling（IBM）

- 表格精度極高
- 適合論文、研究文件

---

| 工具 | 表格 | 速度 | 隱私 |
|---|---|---|---|
| LlamaParse | ⭐⭐⭐⭐⭐ | 快 | ❌ |
| Unstructured | ⭐⭐⭐ | 慢 | ✅ |
| Docling | ⭐⭐⭐⭐⭐ | 中 | ✅ |

---

## 4. 資料清洗工程

### 4.1 文本正規化

- Unicode 修復（ftfy）
- 空白與換行整理

---

### 4.2 結構性雜訊去除

- Header / Footer
- 引用文獻
- 頁碼

---

### 4.3 PII 遮罩

- Email
- 電話
- 信用卡

---

## 5. 進階 Chunking 策略

### 5.1 Fixed + Overlap

- 500 + 50 chars

---

### 5.2 Semantic Chunking

- 依語意相似度切分
- 成本高、品質佳

---

### 5.3 Parent-Child Index

- 小塊檢索
- 大塊生成

---

## 6. 表格與多模態處理

### 表格策略

1. Markdown 序列化
2. 表格摘要 + 原表注入

---

## 7. 總結

> RAG 的成敗，80% 取決於前處理。
