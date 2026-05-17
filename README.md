# Invasive Species Risk Mapping

Binary classification workflow for estimating the distribution risk of *Ambrosia artemisiifolia* across Ukraine using occurrence records and bioclimatic predictors.

## Overview

*Ambrosia artemisiifolia* is a highly invasive and allergenic plant spreading across Eastern Europe. This project builds a species distribution modeling workflow that predicts likely occurrence based on environmental conditions.

The notebook demonstrates:

- Occurrence-data cleaning and geographic filtering.
- Pseudo-absence generation for binary classification.
- WorldClim bioclimatic predictor extraction.
- Logistic Regression and Random Forest model comparison.
- Confusion matrices and feature-importance interpretation.

## Example Results

| Model | Accuracy | ROC-AUC | Precision | Recall | F1 |
|-------|----------|---------|-----------|--------|----|
| Logistic Regression | 0.78 | 0.82 | 0.76 | 0.81 | 0.78 |
| Random Forest | 0.87 | 0.87 | 0.85 | 0.89 | 0.87 |

Random Forest performs best in the notebook experiment, capturing non-linear relationships between bioclimatic variables and species presence.

## Pipeline

```text
1. Data acquisition       GBIF occurrence records
2. Geographic cleaning    Bounding box filtering, deduplication, uncertainty checks
3. Pseudo-absence data    Random background points within the study area
4. Predictor extraction   WorldClim bioclimatic variables
5. Model training         Logistic Regression and Random Forest
6. Evaluation             ROC-AUC, confusion matrix, feature importance
7. Interpretation         Key climatic drivers of species risk
```

## Bioclimatic Predictors

| Variable | Description |
|----------|-------------|
| bio1 | Annual Mean Temperature |
| bio4 | Temperature Seasonality |
| bio5 | Max Temperature of Warmest Month |
| bio12 | Annual Precipitation |
| bio14 | Precipitation of Driest Month |
| bio15 | Precipitation Seasonality |

## Repository Structure

```text
invasive-species-risk-mapping/
├── README.md
├── requirements.txt
├── notebooks/
│   └── species_risk_classification.ipynb
└── figures/
    ├── confusion_matrices.png
    └── rf_feature_importance.png
```

## Quick Start

```bash
git clone https://github.com/llllenah/invasive-species-risk-mapping.git
cd invasive-species-risk-mapping
pip install -r requirements.txt
jupyter notebook notebooks/species_risk_classification.ipynb
```

## Tech Stack

Python, scikit-learn, Rasterio, GBIF data, WorldClim, Pandas, Matplotlib, geospatial analysis.
