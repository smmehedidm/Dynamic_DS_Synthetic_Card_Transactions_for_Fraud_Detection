# Dataset Instructions

The raw datasets used in this project are **not included in this GitHub repository**.

This repository is public, so raw datasets are intentionally kept outside the repository.

## Dataset 01

The Dataset 01 notebook expects the dataset file:

```text
Dataset_01.csv
```

Download the Dataset 01 [source dataset from the original provider](https://www.kaggle.com/datasets/larangetiwari/synthetic-card-transactions-for-fraud-detection/discussion?sort=recent-comments) and place the required CSV file in the local working directory used by the notebook.

The notebook currently loads the file using:

```python
pd.read_csv('Dataset_01.csv')
```

## Dataset 02

Dataset 02 is the ULB European Credit Card Fraud benchmark.

The dataset should be downloaded from its original source.

**Original source:**
[Add the exact source/download link used by the project team here.](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud?utm_source=gemini)

## Dataset 03

Dataset 03 is the Sparkov synthetic credit card transaction dataset.

The dataset should be downloaded from its original source.

**Original source:**
[Add the exact source/download link used by the project team here.](https://www.kaggle.com/datasets/kartik2112/fraud-detection/code)

## Local Data Setup

A typical local setup can be:

```text
Project/
│
├── notebooks/
│   ├── Dataset_01_CREDIT_CARD_FRAUD_DETECTION.ipynb
│   ├── Dataset_02_CREDIT_CARD_FRAUD_DETECTION.ipynb
│   └── Dataset_03_CREDIT_CARD_FRAUD_DETECTION.ipynb
│
├── data/
│   └── README.md
│
└── Dataset_01.csv
```

The exact location may need to be adjusted according to the file paths used in each notebook.

## Important

* Raw datasets are not uploaded to GitHub.
* Do not commit CSV, ZIP, or other large raw dataset files.
* Download datasets only from their original sources.
* Follow the license and usage requirements of each dataset.
* Do not upload private or confidential transaction data.
