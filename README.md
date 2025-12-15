# Personal Finance Analytics Platform (Databricks Lakehouse)

A **Databricks-based personal finance analytics platform** that ingests multi-bank transaction data, applies business logic using PySpark, and produces analytics-ready datasets for dashboards (Google Sheets / BI).

This project is designed to demonstrate **real-world Data Engineering patterns** such as Bronze–Silver–Gold architecture, Delta Lake, and KPI modeling using **actual financial data**.

---

## 🎯 Objectives

This platform focuses on three core goals:

1. **Identify money leakage**

   * Detect discretionary spending patterns
   * Highlight recurring non-essential expenses

2. **Support long-term investment planning**

   * Track investing vs spending trends
   * Monitor savings rate over time

3. **Understand and grow passive income**

   * Automatically derive interest income from bank transactions
   * Measure passive income coverage against mandatory expenses

---

## 🏗️ Architecture Overview

```
Data Sources
├── ICICI Bank CSV Statements
├── IDFC Bank CSV Statements
│
Databricks Lakehouse
├── Bronze Layer  (Raw Ingestion - Delta)
├── Silver Layer  (Cleaned & Categorized)
├── Gold Layer    (Aggregated KPIs)
│
Consumption
├── Google Sheets Dashboards
└── (Optional) Power BI
```

---

## 🧱 Data Layers

### 🥉 Bronze Layer – Raw Ingestion

* Ingests CSV bank statements as-is
* Bank-agnostic schema
* Append-only Delta tables
* Full traceability (`source_file`, `ingest_ts`)

**Table:** `bronze_bank_transactions`

---

### 🥈 Silver Layer – Business Logic

* Normalize debit/credit into signed amounts
* Categorize transactions:

  * Income (Active vs Passive)
  * Mandatory Expenses
  * Discretionary Spending
  * Investments
* Detect money leakage using rule-based flags
* Deduplication and data quality checks

**Key Concepts**

* PySpark transformations
* Regex-based classification
* Financial domain modeling

---

### 🥇 Gold Layer – Analytics & KPIs

Pre-aggregated tables optimized for reporting:

* Monthly cashflow summary
* Money leakage analysis
* Investment allocation snapshot
* Passive income vs mandatory expense coverage

These tables are exported as CSVs and consumed by Google Sheets dashboards.

---

## 📊 Dashboards (Google Sheets)

* **Monthly & Annual Budget Overview**
* **Money Leakage Analysis**
* **Investment Portfolio Summary**
* **Passive Income Growth Tracking**

Google Sheets is used purely as a **presentation layer** — all business logic resides in Databricks.

---

## 🔄 Orchestration

* Monthly Databricks Jobs
* Append-only ingestion
* Idempotent transformations
* Designed to support Airflow integration (future enhancement)

---

## 🛠️ Tech Stack

* **Databricks**
* **Apache Spark (PySpark)**
* **Delta Lake**
* **SQL**
* **Google Sheets** (Reporting)
* **GitHub**

---

## 📁 Project Structure

```
personal-finance-databricks/
│
├── notebooks/
│   ├── 01_bronze_ingestion.py
│   ├── 02_silver_transform.py
│   ├── 03_gold_aggregates.py
│
├── data/
│   └── raw/
│       ├── icici/
│       └── idfc/
│
├── README.md
```

---

## 💡 Why This Project?

* Uses **real personal finance data**, not synthetic datasets
* Demonstrates **end-to-end Data Engineering ownership**
* Balances **automation, cost efficiency, and analytical depth**
* Easily extensible to:

  * Streaming ingestion (Kafka / Kinesis)
  * Advanced anomaly detection
  * GenAI-based financial insights

---

## 🚀 Future Enhancements

* PDF bank statement ingestion (document parsing)
* Streaming transaction ingestion
* ML-based expense classification
* GenAI-powered insights (LangChain / LangGraph)

---

## 👤 Author

Built by a Data Engineer with experience in **Databricks, PySpark, Azure, and Analytics**, focused on designing scalable and cost-efficient data platforms.

---

⭐ If you find this project useful or insightful, feel free to star the repository!
