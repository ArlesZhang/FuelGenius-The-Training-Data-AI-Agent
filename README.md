# FuelGenius — The Training Data AI Agent

[![Python](https://img.shields.io/badge/python-3.11-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Status](https://img.shields.io/badge/status-Beta-yellow)](#)

**Mission**: Make training data as controllable, compilable, and self-evolving as fuel.
**Positioning**: A training data pipeline + intelligent flywheel system designed specifically for AI data engineers.

---

## Project Overview

FuelGenius is a **modular, distributed, high-quality data processing pipeline** focused on AI training data cleaning, augmentation, and quality control.
It forms a **data flywheel**: data cleaning → augmentation → data quality evaluation → feedback optimization → iterative self-evolution, providing high-quality fuel for the downstream Cody Agent.

---

## Core Functional Modules

| Module                                        | Key Technologies                                     | Description                                                                                               |
| --------------------------------------------- | ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **Intelligent Data Exploration & Connectors** | Spark DataFrame API, GitHub API, Web Scraper         | Distributed ingestion of multi-source raw data and statistical metadata extraction.                       |
| **AST-based Syntax & Quality Filtering**      | Tree-sitter, Spark UDF                               | Parallel parsing of code, filtering low-quality samples, and extracting function/variable structure info. |
| **Distributed Approximate Deduplication**     | MinHash LSH, Spark MLlib                             | Efficiently identify and remove similar samples to reduce redundancy.                                     |
| **Sensitive Info & Toxic Content Scanning**   | Regex, NLP Models (Classifier), Spark SQL            | Detect secrets, PII, and toxic content to ensure data safety.                                             |
| **Optimized Output & Partitioning**           | Parquet, Snappy/ZSTD Compression, Partitioning       | Output columnar compressed datasets partitioned by language/license for training efficiency.              |
| **Data Augmentation & Synthesis Module**      | Generative Models, MixUp, SMOTE                      | Automatically generate rare samples to enhance data diversity.                                            |
| **Data Quality & Flywheel Feedback Engine**   | Data Score Metrics, Drift Detection, Active Learning | Monitor data integrity, balance, and noise; feedback optimization rules and augmentation strategies.      |

---

## Project Highlights

* Focused vertical scenario, avoiding the red ocean of generic ETL and Copilot competition
* Modular pipeline, quickly adaptable to new data sources and rules
* Data flywheel mechanism — training data gets smarter with use
* Distributed computation for TB-scale data processing
* Quantifiable business value — showcase your engineering capability in AI data preprocessing

---

## Data Flywheel Architecture

```
Raw Data Ingestion → AST Parsing & Quality Filtering → Deduplication & Sensitive Info Cleaning
↓                                           ↑
Data Augmentation & Synthesis ← Data Quality Monitoring & Feedback ← Training Results & User Interaction Data
```

> The smarter the data becomes, the higher-quality fuel FuelGenius provides to the Cody Agent.

---

## Phase Plan

| Week   | Phase                        | Main Goal                                                                   | Validation Metric                                                 |
| ------ | ---------------------------- | --------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Week 1 | Tech Stack & Env Setup       | Configure Spark, Tree-sitter; implement data ingestion and profiling module | Complete data ingestion demo; generate metadata statistics report |
| Week 2 | Core Dedup & Toxic Cleaning  | Build MinHash dedup module and sensitive/toxic scan module                  | Duplicate rate ↓ ≥50%, sensitive data coverage ≥90%               |
| Week 3 | Output Format & Augmentation | Implement Parquet output, partitioning strategy; generate augmented samples | Versioned dataset output; model generalization ↑ ≥5%              |
| Week 4 | Integration & Documentation  | Integrate pipeline, write blog/tech docs                                    | Full end-to-end run; Blog published                               |

---

## Quick Start

### 1️⃣ Install dependencies

```bash
git clone https://github.com/yourusername/FuelGenius.git
cd FuelGenius
python -m venv venv
source venv/bin/activate  # Linux / macOS
venv\Scripts\activate     # Windows
pip install -r requirements.txt
```

### 2️⃣ Data ingestion example

```python
from fuelgenius.ingest import DataIngestor

ingestor = DataIngestor(source="github_archive")
df_raw = ingestor.fetch_sample(limit=1000)
df_raw.head()
```

### 3️⃣ Data cleaning example

```python
from fuelgenius.clean import DataCleaner

cleaner = DataCleaner()
df_clean = cleaner.run(df_raw)
df_clean.head()
```

### 4️⃣ Data augmentation example

```python
from fuelgenius.augment import DataAugmentor

augmentor = DataAugmentor()
df_aug = augmentor.run(df_clean)
```

---

## Research & Future Directions

* **Data-as-Code & Dataset Compiler**: DSL-based rule definition for reproducible dataset construction
* **LLM-in-the-loop Data Repair**: Auto-generate data cleaning and augmentation code
* **Intelligent Flywheel Validation**: Quantify how cleaning/augmentation improves model performance
* **Cody Agent Integration**: FuelGenius output directly powers Cody for closed-loop automation

---

## Tech Stack

* **Data Processing**: Spark, Polars, DuckDB, Pandas
* **Compilation & DSL Rules**: Python AST / MLIR-lite
* **Generation & Augmentation**: GPT-family / Diffusion / MixUp / SMOTE
* **Storage & Retrieval**: Parquet + Chroma/Weaviate (embedding)
* **Orchestration & Execution**: Airflow / Prefect
* **Monitoring & Visualization**: Streamlit / Gradio / Grafana

---

## Deliverables

* Notebook demo: Raw → Cleaning → Augmentation → Output → Model Comparison
* Data flywheel visualization diagram
* GitHub repo: modular pipeline, DSL examples, dataset versioning demo
* Blog series: *“Building the Data Flywheel — FuelGenius Practical Notes”*
