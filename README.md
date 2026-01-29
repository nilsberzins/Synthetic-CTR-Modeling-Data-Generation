# Synthetic Data Generation for CTR Modeling

This project explores end-to-end data engineering and modeling workflows for **click-through rate (CTR) prediction** using highly imbalanced advertising data. The primary objective is to evaluate strategies for handling rare-event data and to assess whether **synthetic data generation** can improve downstream model performance and generalization.

The project uses a large-scale digital advertising dataset from the **Digix Global AI Challenge**, containing millions of ad impressions with sparse click events.

---

## Project Overview

This workflow focuses on building reliable, reproducible pipelines for preprocessing, modeling, and evaluating highly skewed behavioral data commonly encountered in growth and marketing analytics.

---

## Data Ingestion and Exploration

- Loaded large raw CSV datasets (7M+ rows) and cached intermediate artifacts to enable efficient iteration.
- Performed exploratory analysis to understand data sparsity, skewed class distributions, and feature structure.

---

## Data Pruning and Preparation

- Pruned the dataset to retain users with at least one observed click, improving signal quality.
- Isolated high-activity task subgroups to create more informative modeling subsets.
- Reduced memory usage through data type casting and column pruning to support scalable processing.

---

## Feature Engineering

- Transformed complex list-based categorical features into interpretable count and aggregate statistics.
- Engineered correlated behavioral features to capture interaction intensity while reducing dimensionality.
- Identified and removed low-signal or uninformative features using model-based importance analysis.

---

## Class Imbalance Handling

CTR prediction exhibits extreme class imbalance. The following strategies were evaluated:

- Undersampling combined with class-weighted models
- Synthetic oversampling using **SMOTENC**

Model performance was evaluated using:
- Precision, Recall, and F1-score
- ROC-AUC and PR-AUC

Classification thresholds were tuned to optimize decision-relevant metrics rather than relying on default thresholds.

---

## Predictive Modeling

- Trained **XGBoost classifiers** on stratified train/test splits.
- Emphasized robustness and precision-recall tradeoffs over naive accuracy metrics.
- Analyzed feature importance to understand behavioral drivers of ad clicks.

---

## Synthetic Data Generation

Two synthetic data generation approaches were implemented:

- **CTGAN (Conditional Tabular Generative Adversarial Network)**
- **REaLTabFormer**, a transformer-based model for tabular data

Synthetic data was generated to augment rare click events and improve model training stability.

---

## Synthetic Data Evaluation

Synthetic data quality and utility were evaluated using:

- Feature distribution comparisons between real and synthetic data
- Regularized regression (Lasso) to assess relationship preservation
- Downstream model performance on held-out real data

The impact of varying proportions of synthetic data on model generalization was systematically tested.

---

## Key Takeaways

- CTR prediction involves extreme class imbalance and noisy behavioral signals.
- Thoughtful data pruning and feature engineering materially improve model stability.
- Synthetic data can improve recall and robustness in rare-event settings but requires careful evaluation to avoid degrading real-world performance.
- Pipeline design, metric selection, and monitoring are as important as model choice.

---

## Skills Demonstrated

- Data ingestion and preprocessing at scale  
- Feature engineering on semi-structured behavioral data  
- Handling extreme class imbalance  
- Predictive modeling and threshold optimization  
- Synthetic data generation and evaluation  
- Reproducible, experiment-driven analytics workflows
