# FinSightAI: SEC EDGAR NLP Pipeline (BANA 275)

## 🔗 Project Article (LinkedIn)

We published a detailed article about this project:

👉 [Read the full article on LinkedIn](https://www.linkedin.com/posts/tamarakare-edwin-biayeibo-ba9b65254_nlp-fintech-rag-activity-7440970878605234177-2j3D)

---

This project builds an end-to-end AI-powered pipeline to automatically extract, analyze, and query financial insights from SEC EDGAR filings (e.g., 10-K, 10-Q).

It downloads filings, converts them into clean text, extracts structured financial data, and supports downstream NLP tasks such as:
- financial metric extraction
- retrieval-augmented generation (RAG)
- question answering
- risk classification
- SQL-based financial analysis

---

## Project Motivation

SEC filings are a key source of financial information, but they present major challenges:

- filings often exceed **100+ pages**
- important insights are buried in **unstructured text**
- analysts spend hours manually reading documents
- professional tools can cost **$10K+ per year**

In our project:
- we processed **250+ filings**
- each filing averages **~120 pages**
- key risks appear across **15+ sections**

Our goal is to reduce hours of manual analysis into seconds of automated insights.

---

## Key Features

### Data Pipeline 📥
- Download SEC EDGAR filings
- Convert HTML filings into clean text
- Build structured datasets (JSONL / Parquet)

### Financial Extraction 📊
- We extract key financial metrics:
  - total revenue
  - net income
  - total assets
  - total liabilities
  - cash & equivalents

### RAG + QA 🤖
- Chunk and embed filings
- Retrieve relevant sections
- Generate answers with citations

### Risk Classification ⚠️
- Label risks:
  - regulatory
  - operational
  - financial

### SQL Database 🗄️
- Store structured financial metrics
- Run analytical queries

---

## Project Structure

```bash
edgar-nlp-pipeline/
│
├── data/
│   ├── raw/                 # downloaded raw filings (ignored by git)
│   ├── dataset/             # processed datasets (ignored by git)
│   │   ├── edgar_docs.jsonl
│   │   ├── edgar_docs.parquet
│   │   ├── edgar_meta.json
│   │   └── financial_metrics.jsonl
│   │
│   ├── eval/
│   │   ├── evaluation_queries.json
│   │   └── results/
│   │
│   ├── sql/
│   │   └── finsightai.db
│   │
│   └── top50_sp500.csv
│
├── docs/
│   ├── DATA_SCHEMA.md
│   └── ragworkflow.md
│
├── src/
│   ├── data/
│   │   ├── fetch_top50.py
│   │   ├── clean_top50_csv.py
│   │   └── sec_edgar_pipeline.py
│   │
│   ├── rag/
│   │   ├── build_index.py
│   │   ├── embed_chunks.py
│   │   ├── retrieve.py
│   │   └── section_detector.py
│   │
│   ├── eval/
│   │   ├── evaluate_qa.py
│   │   ├── evaluate_retrieval.py
│   │   ├── evaluate_risk.py
│   │   └── run_evaluation.py
│   │
│   ├── financial_extractor.py
│   ├── sql_database.py
│   ├── qa_pipeline.py
│   ├── qa_gemini.py
│   ├── risk_classifier.py
│   ├── run_data_pipeline.py
│   ├── run_rag_pipeline.py
│   ├── test_query.py
│   └── trend_analyzer.py
│
├── tests/
├── requirements.txt
├── .gitignore
└── README.md

```


## 🛠️ Setup

1. Create virtual environment
```bash
python -m venv .venv
.venv\Scripts\activate
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

## ▶️ Run the Pipeline

### Run data pipeline:
```bash
python src/run_data_pipeline.py
```

### Run RAG pipeline:
```bash
python src/run_rag_pipeline.py
```

### Test query:
```bash
python -m src.test_query
```
