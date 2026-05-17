<h1 align="center">🌿 Invasive Species Risk Mapping</h1>

<p align="center">
  <img src="https://img.shields.io/badge/python-3.10+-blue.svg"/>
  <img src="https://img.shields.io/badge/scikit--learn-classification-F7931E.svg"/>
  <img src="https://img.shields.io/badge/GBIF-occurrence_data-4CAF50.svg"/>
  <img src="https://img.shields.io/badge/WorldClim-bioclimatic-795548.svg"/>
</p>

<p align="center">
  <b>Binary classification pipeline for predicting the distribution risk of <i>Ambrosia artemisiifolia</i> (common ragweed) across Ukraine using GBIF occurrence data and WorldClim bioclimatic predictors.</b>
</p>

---

## 🎯 Overview

*Ambrosia artemisiifolia* is a highly invasive, allergenic plant spreading across Eastern Europe. This project builds a **species distribution model (SDM)** to predict where the plant is likely to occur based on climatic conditions — a common task in environmental risk assessment and public health planning.

## Example Results

| Model | Accuracy | ROC-AUC | Precision | Recall | F1 |
|-------|----------|---------|-----------|--------|----|
| Logistic Regression | 0.78 | 0.82 | 0.76 | 0.81 | 0.78 |
| **Random Forest** | **0.87** | **0.87** | **0.85** | **0.89** | **0.87** |

> Random Forest performs best in the notebook experiment, capturing non-linear relationships between bioclimatic predictors and species presence.

## 🔬 Pipeline

```
1. Data Acquisition     → GBIF API (2000-2024 occurrence records for Ukraine)
2. Geographic Cleaning  → Bounding box filter, deduplication, uncertainty threshold
3. Pseudo-absence       → Random background points within Ukraine's extent
4. Predictor Extraction → 6 WorldClim bioclimatic variables (bio1, bio4, bio5, bio12, bio14, bio15)
5. Model Training       → Logistic Regression + Random Forest (75/25 split)
6. Evaluation           → ROC-AUC, confusion matrix, feature importance
7. Interpretation       → Key climatic drivers of species distribution
```

### Bioclimatic Predictors
| Variable | Description |
|----------|-------------|
| bio1 | Annual Mean Temperature |
| bio4 | Temperature Seasonality |
| bio5 | Max Temperature of Warmest Month |
| bio12 | Annual Precipitation |
| bio14 | Precipitation of Driest Month |
| bio15 | Precipitation Seasonality |

## 🏗 Structure

```
invasive-species-risk-mapping/
├── README.md
├── requirements.txt
├── notebooks/
│   └── species_risk_classification.ipynb
├── data/
│   └── .lab_cache/          # Cached GBIF & WorldClim downloads
└── figures/
    └── *.png                # Feature importance, ROC, maps
```

## 🚀 Quick Start

```bash
git clone https://github.com/llllenah/invasive-species-risk-mapping.git
cd invasive-species-risk-mapping
pip install -r requirements.txt
jupyter notebook notebooks/species_risk_classification.ipynb
```

## 🛠 Tech Stack

`Python` · `scikit-learn` · `Rasterio` · `GBIF API` · `WorldClim` · `Pandas` · `Matplotlib` · `Geospatial Analysis`

## 👤 Author

**Olena Serhiienko** — [@llllenah](https://github.com/llllenah)
