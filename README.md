# FuelGenius — The Training Data AI Agent

[![Python](https://img.shields.io/badge/python-3.11-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Status](https://img.shields.io/badge/status-Beta-yellow)](#)

**使命**：让训练数据像燃料一样可控、可编译、能自我进化。  
**定位**：专为 AI 数据工程师设计的训练数据 Pipeline + 智能飞轮系统。

---

## 项目概览

FuelGenius 是一套 **模块化、分布式、高质量数据处理 Pipeline**，专注于 AI 训练数据清洗、增强与质量控制。  
它形成一个 **数据飞轮**：数据清洗 → 增强 → 数据质量评估 → 反馈优化 → 迭代自进化，为后续 Cody Agent 提供高质量燃料。

---

## 核心功能模块

| 模块 | 涉及技术要点 | 功能说明 |
|------|---------------|-----------|
| **智能数据探查与连接器** | Spark DataFrame API, GitHub API, Web Scraper | 分布式读取多源原始数据，统计元信息。 |
| **基于 AST 的语法与质量过滤** | Tree-sitter, Spark UDF | 并行解析代码，剔除劣质样本，提取函数、变量等结构信息。 |
| **分布式近似去重 (Deduplication)** | MinHash LSH, Spark MLlib | 高效找出相似样本并剔除，解决数据冗余问题。 |
| **敏感信息与毒性内容扫描** | Regex, NLP模型(Classifier), Spark SQL | 检测密钥、PII及毒性内容，保证数据安全。 |
| **训练优化格式输出与分区** | Parquet, Snappy/ZSTD Compression, Partitioning | 输出列式压缩数据集，按语言/许可证分区，便于训练。 |
| **增强与合成数据模块** | Generative Models, MixUp, SMOTE | 自动生成稀缺样本，提高训练集多样性。 |
| **数据质量与飞轮反馈引擎** | Data Score metrics, Drift Detection, Active Learning | 监控数据完整性、平衡性、噪声水平；反馈优化规则和增强策略。 |

---

## 项目亮点

- 专注垂直场景，避开通用 ETL 和 Copilot 红海竞争  
- 模块化 Pipeline，可快速适配新数据源与规则  
- 数据飞轮机制，训练数据越用越智能  
- 分布式计算加速，处理 TB 级数据  
- 商业价值可量化，展示你在 AI 数据前处理上的工程能力  

---

## 数据飞轮架构

```

原始数据采集 → AST 解析 & 质量过滤 → 去重 & 敏感信息清理
↓                                           ↑
数据增强 & 合成 ← 数据质量监控与反馈 ← 训练效果 & 用户交互数据

````

> 数据越用越聪明，FuelGenius 输出的高质量数据直接为 Cody Agent 提供燃料。

---

## 阶段计划表

| 周数 | 阶段 | 主要目标 | 验证指标 |
|------|------|-----------|-----------|
| 第 1 周 | 技术选型与环境搭建 | Spark, Tree-sitter 配置；实现数据摄取与初步统计模块 | 完成基础数据摄取 Demo；生成元信息统计报告 |
| 第 2 周 | 核心去重与毒性清洗 | MinHash 去重模块、敏感信息/毒性扫描模块 | 清洗数据集重复率降低 ≥50%，敏感数据覆盖率 ≥90% |
| 第 3 周 | 格式输出与增强模块 | Parquet 输出，分区策略；生成增强样本 | 输出训练集版本化样本，模型泛化性能提升 ≥5% |
| 第 4 周 | 集成测试与文档 | Pipeline 集成测试，撰写博客/技术文档 | 成功运行 end-to-end 流程；Blog 发布 |

---

## 快速上手

### 1️⃣ 安装依赖
```bash
git clone https://github.com/yourusername/FuelGenius.git
cd FuelGenius
python -m venv venv
source venv/bin/activate  # Linux / macOS
venv\Scripts\activate     # Windows
pip install -r requirements.txt
````

### 2️⃣ 数据摄取示例

```python
from fuelgenius.ingest import DataIngestor

ingestor = DataIngestor(source="github_archive")
df_raw = ingestor.fetch_sample(limit=1000)
df_raw.head()
```

### 3️⃣ 清洗示例

```python
from fuelgenius.clean import DataCleaner

cleaner = DataCleaner()
df_clean = cleaner.run(df_raw)
df_clean.head()
```

### 4️⃣ 数据增强示例

```python
from fuelgenius.augment import DataAugmentor

augmentor = DataAugmentor()
df_aug = augmentor.run(df_clean)
```

---

## 研究与未来方向

* **Data-as-Code & Dataset Compiler**：规则 DSL 化，实现可复现训练集构建
* **LLM-in-the-loop 数据修复**：自动生成数据清洗与增强代码
* **智能飞轮验证**：量化数据增强/清洗对模型性能提升效果
* **Cody Agent 整合**：FuelGenius 输出直接喂给 Cody，实现自动化闭环

---

## 技术栈

* **数据处理**：Spark, Polars, DuckDB, Pandas
* **编译与规则 DSL**：Python AST / MLIR-lite
* **生成与增强**：GPT-family / Diffusion / MixUp / SMOTE
* **存储与检索**：Parquet + Chroma/Weaviate (embedding)
* **调度与执行**：Airflow / Prefect
* **监控与可视化**：Streamlit / Gradio / Grafana

---

## 成果展示

* Notebook Demo：原始表 → 清洗 → 增强 → 输出训练集 → 训练模型对比
* 数据飞轮逻辑可视化图
* GitHub 仓库：模块化 Pipeline、DSL 示例、数据版本化示例
* 博客/技术文章：系列《构建数据飞轮：FuelGenius 实践笔记》

