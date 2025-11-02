## 1️⃣ 完整文件夹结构

```
FuelGenius/
├── README.md
├── LICENSE
├── requirements.txt
├── setup.py
├── example.ipynb
├── data/
│   └── sample_raw.csv          # 示例原始数据
├── fuelgenius/
│   ├── __init__.py
│   ├── ingest.py               # 数据摄取模块
│   ├── clean.py                # 数据清洗模块
│   ├── augment.py              # 数据增强模块
│   ├── utils.py                # 工具函数 (日志、评估指标等)
│   └── config.py               # 配置文件 (路径、参数等)
├── tests/
│   ├── test_ingest.py
│   ├── test_clean.py
│   └── test_augment.py
└── docs/
    └── architecture.md         # 系统架构说明
```

---

## 2️⃣ requirements.txt (示例)

```
pandas>=2.1
numpy>=1.27
pyspark>=3.5
scikit-learn>=1.3
tree-sitter>=0.20
pyyaml>=6.0
tqdm>=4.65
jupyter>=1.0
```

可根据你实际增强/生成模块再添加 `torch`, `transformers` 等依赖。

---

## 3️⃣ setup.py (基本骨架)

```python
from setuptools import setup, find_packages

setup(
    name="fuelgenius",
    version="0.1.0",
    packages=find_packages(),
    install_requires=[
        "pandas>=2.1",
        "numpy>=1.27",
        "pyspark>=3.5",
        "scikit-learn>=1.3",
        "tree-sitter>=0.20",
        "pyyaml>=6.0",
        "tqdm>=4.65"
    ],
    python_requires=">=3.11",
    description="FuelGenius: AI Training Data Pipeline with Smart Flywheel",
    author="Your Name",
    url="https://github.com/yourusername/FuelGenius",
)
```

---

## 4️⃣ Python 模块骨架

### `fuelgenius/__init__.py`

```python
from .ingest import DataIngestor
from .clean import DataCleaner
from .augment import DataAugmentor
```

---

### `fuelgenius/config.py`

```python
DATA_DIR = "data"
RAW_DATA_FILE = f"{DATA_DIR}/sample_raw.csv"
CLEAN_DATA_FILE = f"{DATA_DIR}/sample_clean.csv"
```

---

### `fuelgenius/utils.py`

```python
import pandas as pd

def save_csv(df, path):
    df.to_csv(path, index=False)
    print(f"[INFO] Saved data to {path}")

def load_csv(path):
    df = pd.read_csv(path)
    print(f"[INFO] Loaded data from {path}, shape={df.shape}")
    return df
```

---

### `fuelgenius/ingest.py`

```python
import pandas as pd
from .config import RAW_DATA_FILE

class DataIngestor:
    def __init__(self, source="sample"):
        self.source = source

    def fetch_sample(self, limit=100):
        if self.source == "sample":
            df = pd.read_csv(RAW_DATA_FILE)
            return df.head(limit)
        else:
            raise NotImplementedError("Only sample source is implemented for demo.")
```

---

### `fuelgenius/clean.py`

```python
import pandas as pd
from .utils import save_csv
from .config import CLEAN_DATA_FILE

class DataCleaner:
    def __init__(self):
        pass

    def run(self, df: pd.DataFrame):
        # 简单清洗示例
        df_clean = df.dropna().drop_duplicates()
        save_csv(df_clean, CLEAN_DATA_FILE)
        return df_clean
```

---

### `fuelgenius/augment.py`

```python
import pandas as pd

class DataAugmentor:
    def __init__(self):
        pass

    def run(self, df: pd.DataFrame):
        # 简单增强示例：复制一遍数据作为 demo
        df_aug = pd.concat([df, df])
        return df_aug
```

---

## 5️⃣ 示例数据 `data/sample_raw.csv`

```csv
id,name,value
1,Alice,10
2,Bob,15
3,Charlie,20
4,,25
5,Alice,10
```

---

## 6️⃣ Jupyter 快速上手示例 `example.ipynb`

```python
from fuelgenius.ingest import DataIngestor
from fuelgenius.clean import DataCleaner
from fuelgenius.augment import DataAugmentor

# 1. 摄取数据
ingestor = DataIngestor()
df_raw = ingestor.fetch_sample(limit=5)
print("原始数据：")
print(df_raw)

# 2. 清洗数据
cleaner = DataCleaner()
df_clean = cleaner.run(df_raw)
print("清洗后数据：")
print(df_clean)

# 3. 数据增强
augmentor = DataAugmentor()
df_aug = augmentor.run(df_clean)
print("增强后数据：")
print(df_aug)
```

---

✅ 这样就有：

* **完整文件夹结构**
* **模块化 Python 骨架**
* **示例数据和 Jupyter Demo**
* **开箱可运行的清洗 + 增强流程**
* README 已经对齐你之前设定的融合版风格

---

Next step :再生成 **高级版本**，加入 **分布式 Spark 支持、AST解析、MinHash去重、毒性扫描等高级功能骨架**，直接可以跑 TB 级数据 Demo，并且完整连接 Cody Agent 的接口。
