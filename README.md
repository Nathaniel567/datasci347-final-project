# Trends Across Loan Application Outcomes

**DATASCI 347: Machine Learning, Fall 2026, Final Project**

**Team:** Landon Minkow, Nathaniel Schrader, Aryn Xing, Lola Pawar

## Abstract

*TBD.* A few sentences summarizing the project, for example: we use 2016 HMDA mortgage application records to predict whether a loan application is approved or denied, examine whether approval patterns differ across applicant demographics and geography, and compare what we find with today's mortgage market.

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Setup](#2-setup)
3. [Results](#3-results)
4. [Discussion](#4-discussion)
5. [Conclusion](#5-conclusion)
6. [References](#6-references)
- [Repository Structure](#repository-structure)
- [How to Reproduce](#how-to-reproduce)
- [Timeline and Division of Work](#timeline-and-division-of-work)

---

## 1. Introduction

### 1.1 What is the problem?

**Research question:** Are there predictable biases or patterns behind which loans get approved in a year without major economic shocks (2016), and how do those findings compare to the loan market today?

Areas we explore:

- Potential bias tied to the demographics of the loan applicant
- Geographic trends in approval
- Predicting the outcome of a loan application from key inputs

### 1.2 Why is this problem interesting?

We chose 2016 because it reflects the mortgage market in a "stable" year:

- It falls well after the 2008 recession.
- It falls well before the pandemic.

The question is still relevant now: mortgage yields are at record highs and interest rates keep rising. Understanding what drove approvals in a stable year gives us a baseline for comparing against today's market.

*TBD: broader use cases (fair lending audits, lender risk models, policy).*

### 1.3 Proposed approach

| # | Approach | Purpose |
|---|----------|---------|
| 01 | EDA / Clustering | An exploratory look at variable distributions and at whether certain applicant profiles are associated with different approval rates |
| 02 | Logistic Regression (Logit) | Estimates how each applicant characteristic shifts the odds of approval for the binary outcome, which gives an interpretable baseline |
| 03 | Classification Tree, Random Forest & Boosting | Predicts the loan outcome category from demographic and geographic features, and captures interactions that logit misses |
| 04 | 2026 External Articles for Context | Compares the historical relationships with the current mortgage market, using qualitative sources to interpret our results |

### 1.4 Why this approach?

*TBD: compare with prior work on HMDA / mortgage approval prediction and explain how our approach differs.*

### 1.5 Key components and limitations

**Limitations:**

- Credit scores and related information are mostly missing from the dataset.
- Current (2026) census and mortgage data are not all published yet.
- Logistic regression misses interactions between features.
- Random forest / boosting: *TBD*
- All models show correlation, not causation.
- The classes are imbalanced: approvals outnumber denials.
- With more time, we might survey homeowners for a broader perspective.

---

## 2. Setup

### 2.1 Dataset

**Source:** [Home Mortgage Disclosure Act (HMDA) Loan Application Register](https://www.consumerfinance.gov/data-research/hmda/), 2016 data. See [`data/README.md`](data/README.md) for download instructions.

| Statistic | Value |
|-----------|-------|
| Rows in our subset (first-lien, owner-occupied, 1–4 family) | 7,036,352 (~7.04M) |
| Columns (HMDA codes) per application | 45 (loan, applicant, location, lender, census tract) |
| Reporting lenders | 6,772 (banks, savings associations, credit unions, mortgage companies) |

**Target, Action Taken:** approved (originated or approved) vs. denied. We drop withdrawn applications, incomplete files, and purchased loans.

**Features:** mostly categorical codes, plus loan amount and income. Features of interest:

- Loan type and loan amount
- Loan purpose (purchase / home improvement / refinancing)
- Property type
- State and county codes (location)
- Applicant demographics (ethnicity, race, sex, income)
- Reasons for denial
- Population information for the property's census tract

*TBD: summary statistics, class balance, and missingness.*

### 2.2 Experimental setup

*TBD: models, hyperparameters, train/validation/test split, cross-validation scheme, evaluation metrics (e.g., accuracy, AUC, F1 for imbalanced classes), and computing environment (Google Colab).*

### 2.3 Problem setup

*TBD: binary classification setup, preprocessing and encoding steps, how class imbalance is handled.*

---

## 3. Results

### 3.1 Main results

*TBD.*

### 3.2 Supplementary results

*TBD: parameter choices and why we made them.*

---

## 4. Discussion

*TBD.*

---

## 5. Conclusion

*TBD.*

---

## 6. References

- CFPB, HMDA data: https://www.consumerfinance.gov/data-research/hmda/
- FFIEC announces availability of 2016 data on mortgage lending: https://www.consumerfinance.gov/archive/newsroom/ffiec-announces-availability-2016-data-mortgage-lending/
- FFIEC publishes 2023 data on mortgage lending: https://www.consumerfinance.gov/archive/newsroom/ffiec-publishes-2023-data-on-mortgage-lending/
- *TBD: papers, articles (e.g., current mortgage market coverage), and repositories we use.*

---

## Repository Structure

```
.
├── README.md            # Project documentation (this file)
├── requirements.txt     # Python dependencies
├── data/
│   ├── README.md        # How to download and subset the HMDA 2016 data
│   ├── raw/             # Raw downloaded data (not committed)
│   └── processed/       # Cleaned data (not committed)
├── notebooks/           # Jupyter notebooks for EDA and modeling
├── src/                 # Reusable code for cleaning, features, and models
├── results/
│   └── figures/         # Saved plots and tables
└── docs/                # Proposal slides, data dictionary notes
```

## How to Reproduce

```bash
git clone https://github.com/Nathaniel567/datasci347-final-project.git
cd datasci347-final-project
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

1. Download the 2016 HMDA data as described in [`data/README.md`](data/README.md) and place it in `data/raw/`.
2. Run the notebooks in `notebooks/` in numeric order. *TBD.*

## Timeline and Division of Work

| Phase | Target date | Tasks |
|-------|-------------|-------|
| Acquire & Clean | ~Nov 8 | Download the 2016 subset and decode fields; build the approved/denied target; handle missing values |
| Explore & Cluster | ~Nov 15 | Visualize approval trends across demographics and loan characteristics; cluster applicants by shared characteristics; compare approval rates across groups to find potential disparities |
| Model | ~Nov 30 | Train a random forest classifier to predict the loan outcome; use gradient boosting to improve performance; compare model outputs with what 2026 articles report about current approvals |
| Compare & Present | ~Dec 1–5 | Interpret model outputs in light of macroeconomic and social trends; put the findings in a presentable format; prepare the final presentation and required uploads |

**Division of work:** *TBD.*
