# Temporal Validation and Cyclic Time Features in Credit Card Fraud Detection

## A Cross-Dataset Study of Model Challenge Under Distribution Shift

This repository contains the implementation, experiments, results, and documentation for a cross-dataset study of credit card fraud detection under temporal distribution shift.

The project investigates how **validation strategy** and **cyclic temporal features** affect machine learning performance when fraud detection models are evaluated on future, unseen transactions.

Three datasets with different observation periods and characteristics are studied:

* **Dataset 01:** Synthetic 6-month credit card transaction dataset
* **Dataset 02:** ULB European credit card fraud benchmark covering approximately 48 hours
* **Dataset 03:** Sparkov synthetic credit card transaction dataset covering approximately 18 months

The study compares **random splitting and chronological splitting**, with and without cyclic temporal features, across Logistic Regression, Random Forest, and XGBoost models.

---

## Research Question

> How does temporal validation affect reported fraud detection performance, and under what conditions do cyclic time features improve fraud detection models under distribution shift?

---

## Project Objectives

The main objectives of this study are:

1. Compare random and chronological validation strategies across three credit card fraud datasets.
2. Investigate the effect of cyclic temporal features such as:

   * `Hour_sin`
   * `Hour_cos`
   * `Weekday_sin`
   * `Weekday_cos`
3. Compare Logistic Regression, Random Forest, and XGBoost under temporal distribution shift.
4. Evaluate model performance using fraud-sensitive metrics such as F1-score, Precision, Recall, PR-AUC and MCC.
5. Optimize classification thresholds using a held-out validation set.
6. Use SHAP explainability to investigate important predictors and the contribution of temporal features.
7. Examine whether conclusions remain consistent across datasets with different time spans and fraud distributions.

---

## Datasets

| Dataset    | Type                 | Observation Period |    Transactions | Fraud Rate |
| ---------- | -------------------- | -----------------: | --------------: | ---------: |
| Dataset 01 | Synthetic            |           6 months | 499,998 cleaned |      0.42% |
| Dataset 02 | Real-world benchmark |           48 hours | 283,726 cleaned |     0.167% |
| Dataset 03 | Synthetic            |         ~18 months |       1,296,675 |      0.58% |

Dataset 01 is based on the LarangeTiwari synthetic credit card transaction dataset.

Dataset 02 is the ULB European credit card fraud benchmark.

Dataset 03 is the Sparkov synthetic credit card transaction dataset.

The original datasets are not included in this repository. Please refer to `data/README.md` for dataset sources and preparation instructions.

---

## Methodology

The project follows a CRISP-DM-oriented workflow:

```text
Business Understanding
        ↓
Data Understanding
        ↓
Data Cleaning
        ↓
Exploratory Data Analysis
        ↓
Feature Engineering
        ↓
Temporal / Random Splitting
        ↓
Class Balancing
        ↓
Model Training
        ↓
Threshold Optimization
        ↓
Test Evaluation
        ↓
SHAP Explainability
```

A strict chronological validation protocol is used to simulate the practical situation where a model is trained on historical transactions and evaluated on future transactions.

For most datasets, the chronological split follows:

```text
70% Training
15% Validation
15% Test
```

The ULB dataset uses a different partition because of its short 48-hour observation period and limited number of fraudulent transactions.

All data-dependent transformations are designed to avoid using future test information during model development.

---

## Experimental Design

The experiments vary several factors:

### Validation Strategy

* Random split
* Chronological split

### Feature Configuration

* Original / non-cyclic features
* Cyclic temporal features

### Models

* Logistic Regression
* Random Forest
* XGBoost

### Class Balancing

Depending on the dataset and experiment:

* No balancing
* Class weighting
* Oversampling / resampling techniques

### Explainability

SHAP is used to investigate model feature importance and determine whether engineered temporal features contribute strongly to fraud predictions.

---

## Cyclic Temporal Features

Time-of-day and day-of-week information are represented using sinusoidal encoding.

Instead of treating hour values as independent integers, the project represents the circular nature of time using:

```text
Hour_sin
Hour_cos
Weekday_sin
Weekday_cos
```

This allows the model to represent the relationship between values such as 23:00 and 00:00 more naturally.

The study does not assume that cyclic features will always improve performance. Their usefulness is evaluated separately under different datasets and validation protocols.

---

## Evaluation Metrics

Because credit card fraud datasets are highly imbalanced, accuracy is not treated as the primary performance measure.

The project evaluates:

* F1-Score
* Precision
* Recall
* PR-AUC
* MCC
* ROC-AUC
* Confusion Matrix

Decision thresholds are optimized on the validation partition and then kept fixed for final test evaluation.

---

## Key Findings

The experiments demonstrate that validation strategy can substantially affect reported fraud detection performance.

For the long-horizon Sparkov dataset, the difference between random and chronological evaluation produced F1 gaps ranging approximately from **0.086 to 0.332** across the tested configurations.

The study also found that cyclic temporal features were highly data-dependent. Their effect differed between random and chronological validation and between datasets.

The final analysis identified Random Forest as one of the comparatively stable models across the studied datasets, while XGBoost showed greater sensitivity to distribution changes in the experimental results.

SHAP analysis further showed that the importance of temporal features depended strongly on the characteristics of the dataset. In the long-horizon Sparkov dataset, `Hour_sin` and `Hour_cos` appeared among the most important predictors.

These findings highlight the importance of evaluating fraud detection models using a validation protocol that reflects the intended temporal deployment setting.

---

## Explainability

SHAP (SHapley Additive exPlanations) is used to investigate model predictions.

The analysis includes:

* Global feature importance
* SHAP summary / beeswarm plots
* Contribution of engineered temporal features
* Comparison of important predictors across datasets

For example, the SHAP analysis of Dataset 03 identified `Hour_sin` and `Hour_cos` among the most important features.

---

## Repository Structure

```text
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   ├── Dataset_01_CREDIT_CARD_FRAUD_DETECTION.ipynb
│   ├── Dataset_02_CREDIT_CARD_FRAUD_DETECTION.ipynb
│   └── Dataset_03_CREDIT_CARD_FRAUD_DETECTION.ipynb
│
├── data/
│   └── README.md
│
├── results/
│   ├── dataset_01/
│   ├── dataset_02/
│   └── dataset_03/
│
├── figures/
│   ├── dataset_01/
│   ├── dataset_02/
│   ├── dataset_03/
│   └── comparison/
│
├── reports/
│   └── Dynamic_DS_Credit_Card_Fraud_Detection_Report.pdf
│
└── docs/
    ├── methodology.md
    ├── dataset_description.md
    └── experiment_design.md
```

---

## Installation

Clone the repository:

```bash
git clone YOUR_REPOSITORY_URL
cd TEMPORAL-FRAUD-DETECTION
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment on Windows:

```bash
venv\Scripts\activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

---

## Main Technologies

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* Imbalanced-learn
* SHAP
* Matplotlib
* Seaborn
* Jupyter Notebook

The experiments were developed using Python 3.13 and the major machine learning libraries documented in the project report.

---

## Reproducibility

The experiments use a fixed random seed:

```text
Random Seed = 42
```

The same experimental framework is applied across the three datasets wherever the dataset structure permits.

The chronological evaluation protocol prevents future observations from being used during model development.

---

## Limitations

This study has several limitations:

* Two of the three datasets are synthetic.
* The ULB dataset covers only approximately 48 hours.
* The study does not include sequential deep learning architectures such as LSTM, GRU, or Transformer models.
* Formal confidence intervals and paired statistical significance tests were not calculated.
* Model hyperparameters were kept consistent between random and chronological experiments to isolate the effect of validation strategy.
* SHAP analysis was performed for selected configurations rather than every experimental combination.

Therefore, the results should be interpreted as a methodological cross-dataset study rather than a complete production fraud detection system.

---

## Team

### Dynamic DS

| Member               | Role                                  |
| -------------------- | ------------------------------------- |
| Mohammad Sourav      | Modeling / Machine Learning           |
| Shehab Mahmud Mehedi | EDA / Feature Engineering             |
| Abul Kalam Azad      | Evaluation / Explainability           |
| Samayel Fayed        | Report / Presentation / Documentation |

**Course:** PGDDS 203 – Data Science Project
**Program:** Postgraduate Diploma in Data Science (PGDDS)
**Institute:** United International University (UIU)
**Supervisor:** Mr. Ahmed Imran Kabir, Assistant Professor

---

## Academic Context

This project was completed as part of the **PGDDS 203 – Data Science Project** at United International University.

The repository is intended for academic reproducibility, learning, research reference, and further experimentation.

---

## References

The full list of academic references is available in the project report.

Important methodological areas include:

* Credit card fraud detection
* Temporal validation
* Concept drift
* Class imbalance
* Cyclic temporal feature engineering
* Ensemble learning
* SHAP explainability

See the project report in `reports/` for the complete reference list.
