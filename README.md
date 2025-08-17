# Credit Card Fraud Detection (Kaggle) 

This repo shows a simple, practical workflow to spot likely credit card fraud using the popular Kaggle dataset and PyOD. 

> open **`PYOD_Fraud_Detect.ipynb`**, run the cells top‑to‑bottom, and check the charts (ROC, Precision–Recall, Reconstruction Error, Confusion Matrix) inside outputs folder.

---

## What’s inside

- **`PYOD_Fraud_Detect.ipynb`** — main notebook (training + evaluation)
- **`requirements.txt`** — Python packages
- **`/outputs/`** — save charts here (ROC, PR, reconstruction error, confusion matrix)
- **`/data/`** — place the Kaggle CSV here (see below)

---

## Data

We use the **Kaggle Credit Card Fraud Detection** dataset 

- Filename is  `creditcard.csv` in the directory path /data/*.csv.

---

## Steps to setup

1) **Create a virtual environment (recommended)**  
```bash
python -m venv .venv
source .venv/bin/activate
```

2) **Install packages**  
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

3) **Add the data**  
- Put the Kaggle CSV into `./data/creditcard.csv`

4) **Run the notebook**  
```bash
jupyter lab
```
Run cells top to bottom.

---

## How it works (high level)

- **Load & split** the data with stratification so the tiny fraud rate is kept in both train and test.
- **Scale** features to make models behave well.
- **Train** one or more detectors, for example:
  - **PyOD** models for anomaly detection.
  - A small **autoencoder** that learns “normal” transactions; high reconstruction error can signal fraud.
  
- **Pick a threshold** using Precision–Recall trade‑offs (we lean toward **higher recall** to miss fewer fraud cases, while keeping precision reasonable).
- **Evaluate** with:
  - **ROC AUC** and **PR AUC**
  - **Precision, Recall, F1**
  - **Confusion matrix**
  - **Reconstruction error distribution** (for the autoencoder)

---


## Reproducing results

- Make sure `requirements.txt` is installed.
- Use the same **random seeds** and **train/test split** for consistent metrics.
---

## Dependencies
- numpy>=1.24
- pandas>=1.5
- scikit-learn>=1.3
- matplotlib>=3.7
- pyod>=1.1.3

- tensorflow==2.16.1
- torch>=2.2.0
- tqdm>=4.65

---
