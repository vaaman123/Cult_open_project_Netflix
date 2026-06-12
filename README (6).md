# 🎬 Netflix Prize — Recommendation System

**Recommendation Systems for Personalized Content Discovery**  
Netflix Prize Dataset · Collaborative Filtering · Matrix Factorization · Neural CF
**Vaaman Sonathi, Ronith Netalkar, EPh 3rd year**
---

## Project Structure

```
netflix-recsys/
├── data/                  ← Place Netflix Prize files here
│   ├── combined_data_1.txt
│   ├── combined_data_2.txt
│   ├── combined_data_3.txt
│   ├── combined_data_4.txt
│   └── movie_titles.csv
├── outputs/               ← Auto-created; stores parquet files & plots
├── models/                ← Auto-created; stores trained model checkpoints
├── 01_eda.ipynb           ← Exploratory Data Analysis
├── 02_modeling.ipynb      ← Model training & recommendation generation
├── 03_evaluation.ipynb    ← RMSE, MAP@10, analysis
├── requirements.txt
└── README.md
```

---

## Models

| Model | Type | Library |
|-------|------|---------|
| **SVD** | Matrix Factorization | scikit-surprise |
| **NeuMF** | Neural Collaborative Filtering (GMF + MLP) | PyTorch |

---

## Evaluation Metrics

| Metric | Definition |
|--------|------------|
| **RMSE** | Root Mean Squared Error on held-out ratings |
| **MAP@10** | Mean Average Precision @ 10 (relevance threshold: rating ≥ 3.5) |

---

## Setup

```bash
pip install -r requirements.txt
```

### Download the dataset
1. Go to https://www.kaggle.com/datasets/netflix-inc/netflix-prize-data
2. Download and extract into `./data/`

---

## Run Order

```
01_eda.ipynb          # EDA + saves processed data to outputs/
02_modeling.ipynb     # Trains SVD + NeuMF, generates Top-10 recs
03_evaluation.ipynb   # Computes RMSE + MAP@10, qualitative analysis
```

Each notebook reads from `./outputs/` (written by the previous notebook).

---

## Configuration

In each notebook, edit the top-level **Config** cell to adjust:

| Parameter | Default | Effect |
|-----------|---------|--------|
| `DATA_DIR` | `./data` | Path to Netflix Prize files |
| `MIN_USER_RATINGS` | 50 | Users with fewer ratings are excluded |
| `MIN_MOVIE_RATINGS` | 100 | Movies with fewer ratings are excluded |
| `MAX_RATINGS` | 2,000,000 | Cap on total ratings (memory safety) |
| `NCF_EPOCHS` | 15 | NeuMF training epochs |
| `NCF_EMBED_DIM` | 64 | Embedding dimension |

---

## Requirements

See `requirements.txt`. Key packages:
- `torch` (GPU recommended)
- `scikit-surprise`
- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `tqdm`, `pyarrow`
