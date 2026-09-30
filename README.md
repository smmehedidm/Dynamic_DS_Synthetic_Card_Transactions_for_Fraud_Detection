# Temporal Validation and Cyclic Time Features in Credit Card Fraud Detection

### A Cross-Dataset Study of Model Robustness Under Distribution Shift

This project investigates how validation strategy and cyclic temporal features affect machine learning performance in credit card fraud detection.

The study compares random and chronological validation approaches across three datasets and evaluates Logistic Regression, Random Forest, and XGBoost. It also explores class imbalance handling, validation-based threshold selection, and model explainability using SHAP.

---

## 2. Research Question

> How does chronological validation compared with random validation affect credit card fraud detection performance, and under what conditions do cyclic temporal features improve model performance?

---

## Research Objectives

* Compare random and chronological data splitting.
* Investigate the effect of cyclic time features.
* Compare Logistic Regression, Random Forest, and XGBoost.
* Evaluate model performance under temporal distribution shift.
* Use SHAP to examine important model features.

## Datasets

The study uses three datasets with different temporal characteristics.

| Dataset    | Description                                | Approx. Observation Period |
| ---------- | ------------------------------------------ | -------------------------: |
| Dataset 01 | Synthetic credit card transactions         |                   6 months |
| Dataset 02 | ULB European credit card fraud benchmark   |                   48 hours |
| Dataset 03 | Sparkov synthetic credit card transactions |                  18 months |

### Dataset 01

The first dataset is a synthetic credit card transaction dataset containing approximately 500,000 transactions.

After duplicate transaction IDs were removed, the dataset contains approximately **499,998 transactions**.

The fraud rate is approximately **0.42%**.

### Dataset 02

Dataset 02 is the ULB European credit card fraud benchmark.

It contains anonymized PCA-based transaction features together with transaction time and amount.

The dataset covers approximately **48 hours** and contains a very small proportion of fraudulent transactions.

### Dataset 03

Dataset 03 is the Sparkov synthetic credit card transaction dataset.

It covers approximately **18 months** and contains approximately **1.3 million transactions**.

The longer observation period provides an opportunity to investigate temporal distribution changes over time.

### Data Availability

Raw datasets are **not stored in this public repository**.

See:

**[`data/README.md`](data/README.md)**

for information about the original dataset sources and download instructions.

---

## Methodology

The project investigates:

* Data cleaning and preprocessing
* Exploratory data analysis
* Cyclic temporal feature engineering
* Class imbalance handling
* Random and chronological validation
* Model training and comparison
* Validation-based threshold selection
* Evaluation using classification metrics
* SHAP-based model explainability

### Models

* Logistic Regression
* Random Forest
* XGBoost

### Temporal Features

Cyclic time features represent recurring time patterns, including the hour of the day and day of the week.

The study uses sinusoidal transformations such as:

* `hour_sin`
* `hour_cos`
* `weekday_sin`
* `weekday_cos`

## Evaluation

The study uses metrics including:

* Precision
* Recall
* F1-score
* PR-AUC
* MCC
* ROC-AUC
* Confusion matrix

## Repository Structure

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── Dataset_01_CREDIT_CARD_FRAUD_DETECTION.ipynb
│   └── Dataset_02_CREDIT_CARD_FRAUD_DETECTION.ipynb
│   └── Dataset_03_CREDIT_CARD_FRAUD_DETECTION.ipynb
├── data/
│   └── README.md
├── results/
└── figures/
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/smmehedidm/Temporal_Credit_Card_Fraud_Detection.git
cd Temporal_Credit_Card_Fraud_Detection
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it:

**Windows**

```bash
.venv\Scripts\activate
```

**macOS/Linux**

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the datasets

Follow the instructions in [`data/README.md`](https://github.com/smmehedidm/Temporal_Credit_Card_Fraud_Detection/tree/main/data). Place the downloaded files in the expected local locations and update notebook paths if necessary.

### 5. Run the notebook

Open Jupyter Notebook:

```bash
jupyter notebook
```

Navigate to the `notebooks/` folder and open the available notebook.

## Reproducibility

The project report describes a fixed random seed and a validation-based approach to threshold selection. For reproducible results, use the same dataset versions, preprocessing steps, package environment, and experiment settings.

## Limitations

* Two of the datasets are synthetic.
* The ULB dataset covers a comparatively short observation period.
* The study focuses on tabular machine learning rather than deep sequential models.
* Results may not generalize to all real-world transaction environments.

## Team — Dynamic DS

| Member               |
| -------------------- |
| Mohammad Sourav      |
| Shehab Mahmud Mehedi |
| Abul Kalam Azad      |
| Samayel Fayed        |

## Academic Context

**Course:** PGDDS 203 – Data Science Project
**Program:** Postgraduate Diploma in Data Science (PGDDS)
**Institution:** United International University (UIU)
**Supervisor:** Mr. Ahmed Imran Kabir, Assistant Professor
