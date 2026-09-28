# Temporal Validation and Cyclic Time Features in Credit Card Fraud Detection

### A Cross-Dataset Study of Model Performance Under Distribution Shift

This project investigates how validation strategy and cyclic temporal features affect machine learning performance in credit card fraud detection.

The study compares random and chronological validation approaches across three datasets and evaluates Logistic Regression, Random Forest, and XGBoost. It also explores class imbalance handling, validation-based threshold selection, and model explainability using SHAP.

## Research Objectives

* Compare random and chronological data splitting.
* Investigate the effect of cyclic time features.
* Compare Logistic Regression, Random Forest, and XGBoost.
* Evaluate model performance under temporal distribution shift.
* Use SHAP to examine important model features.

## Datasets

The study uses three datasets:

| Dataset    | Description                                                      |
| ---------- | ---------------------------------------------------------------- |
| Dataset 01 | Synthetic card transactions, approximately six months            |
| Dataset 02 | ULB European credit card fraud benchmark, approximately 48 hours |
| Dataset 03 | Sparkov synthetic transactions, approximately 18 months          |

Raw datasets are not included in this repository. See [`data/README.md`](data/README.md) for download instructions.

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
git clone https://github.com/smmehedidm/Dynamic_DS_Synthetic_Card_Transactions_for_Fraud_Detection.git
cd Dynamic_DS_Synthetic_Card_Transactions_for_Fraud_Detection
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

Follow the instructions in [`data/README.md`](data/README.md). Place the downloaded files in the expected local locations and update notebook paths if necessary.

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
