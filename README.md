# Synthetic Identity Fraud Detection

End-to-end fraud scoring pipeline on the [IEEE-CIS Fraud Detection](https://www.kaggle.com/competitions/ieee-fraud-detection) dataset.

**Dataset:** 590,540 transactions, 3.50% fraud positive rate, severe class imbalance.

---

## Results

_To be filled in as the project develops._

- **PR-AUC:** TBD (logistic baseline: TBD)
- **Capture rate @ 1% FPR:** TBD
- **Cost-optimal threshold:** TBD

---

## Approach

This project frames fraud detection as a binary classification problem on heavily imbalanced transactional data, with explicit attention to fraud-operations tradeoffs that pure accuracy metrics obscure.

### Modeling Philosophy

- Optimize for **PR-AUC**, not ROC-AUC (often misleading under severe imbalance).
- Evaluate **capture rate at fixed false-positive budgets**, reflecting real fraud operations.
- Use **cost-sensitive thresholding** to balance fraud loss vs manual review cost.
- Apply a **time-based train/test split** to reduce temporal leakage.

---

## Features

Three feature families designed to reflect production fraud systems:

### Identity Consistency
- Email domain mismatches between purchaser and recipient
- Freemail provider flags
- Card/address consistency frequency

### Velocity
- Transaction count in rolling 24h / 7d windows
- Spend amount in rolling 24h / 7d windows
- Rapid repeat attempts by identity or address

### Device Linkage
- Device fingerprint reuse
- Browser / OS reuse patterns
- Anonymized network identifier reuse

---

## Repo Structure

```text
synthetic-identity-fraud-detection/
├── data/
│   ├── raw/          # IEEE-CIS CSVs (gitignored)
│   └── processed/    # Engineered datasets (gitignored)
├── notebooks/        # EDA and experimentation
├── src/
│   ├── features.py   # Feature engineering
│   ├── train.py      # Model training
│   ├── evaluate.py   # Metrics/threshold tuning
│   └── api.py        # FastAPI scoring service
├── models/           # Saved models (gitignored)
├── tests/            # API tests
├── reports/
│   └── figures/      # Charts / SHAP plots
├─requirements.txt
└── README.md
```

---

## Setup

Requires Python 3.11.

bash
git clone https://github.com/chibuzorwilliams/synthetic-identity-fraud-detection.git
cd synthetic-identity-fraud-detection

python3.11 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt


Download the IEEE-CIS dataset from [Kaggle](https://www.kaggle.com/competitions/ieee-fraud-detection/data) and place the CSVs in data/raw/.

## Deployment

To be added in the deployment phase.

## Limitations & next steps

To be filled in honestly as the project develops. Strong portfolio projects acknowledge what they didn't do.

---

*Author:* Chibuzor Williams
 · [LinkedIn](https://linkedin.com/in/chibuzorwilliams)
 · [Email](mailto:williamschibuzor15@gmail.com)
