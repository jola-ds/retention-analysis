# 📊 Subscription Retention & Survival Analysis (KKBOX)

This project aims to analyse subscriber retention and forecast equity using survival modeling and other techniques.

**Goal:** Understand when and why customers churn in a subscription business, and forecast long-term retention using survival analysis and probabilistic models.

**Why this matters:** Most churn analyses treat churn as a binary outcome. This project reframes churn as a time-to-event problem, accounting for right censoring and lifecycle dynamics.

## Business Context

- KKBOX is a contractual, subscription-based music streaming service

- Users renew monthly (auto or manual)

- Churn occurs when a user cancels or fails to renew

- Observation windows limit what we can directly observe

**Note:** Users who haven’t churned yet are not “retained forever”, their churn time is only unknown.

## Core Questions

- When does churn primarily occur in the customer lifecycle?

- How does auto-renewal affect churn risk over time?

- Which early behaviors signal higher churn risk?

- How long will current cohorts continue to generate value?

## Dataset

Source:
WSDM – KKBOX Churn Prediction Challenge

Tables:

- transactions — subscription activity and renewals

- members — user demographics

- user_logs — listening behavior (used for early engagement features)

**Note:** This dataset contains multiple transactions per user, requiring careful aggregation and time alignment.

## Analytical Approach

### Step 1 — Data Understanding & Cleaning

- Validate time fields

- Identify structural missingness

- Handle outliers conservatively

- Preserve information for censoring

### Step 2 — Cohort Analysis

- Group users by calendar join month

- Measure retention in relative time

- Identify lifecycle churn patterns

### Step 3 — Survival Analysis (Kaplan–Meier)

- Model churn as a time-to-event

- Account for right-censored users

- Compare survival curves across user segments

### Step 4 — Risk Modeling (Cox Proportional Hazards)

- Quantify churn risk factors

- Interpret hazard ratios

- Validate model assumptions

### Step 5 — Retention Forecasting

- Estimate long-term retention using sBG

- Forecast customer lifetime

- Translate retention into business insight

## Key Findings (To Be Completed)

Leave this as a placeholder early on.

Examples:

Churn is heavily concentrated in the first X months

Auto-renew users have significantly lower churn risk

Early engagement is predictive of survival

Retention stabilizes after an initial drop-off

## Tools & Libraries

- Python
- pandas, numpy
- lifelines
- matplotlib, seaborn
- scipy

## Related Article

📖 “Churn Is a Time Problem: Modeling Subscription Retention with Survival Analysis”
(link coming soon)

## Next Steps

- Segment-specific survival models
- Time-varying covariates
- Revenue-weighted churn analysis
- Product intervention simulations

## Getting Started

1. Install dependencies: `pip install -r requirements.txt`
2. Explore notebooks in the `notebooks/` directory.

## Repository Structure

```text
kkbox-retention-analysis/
│
├── data/
│   ├── raw/
│   └── processed/
│       └── sbg_input.csv
│
├── src/
│   ├── preprocessing/
│   │   └── build_sbg_input.py
│   │
│   ├── models/
│   │   ├── sbg.py
│   │   ├── survival.py
│   │   └── cox.py
│
├── notebooks/
│   ├── 01_exploration.ipynb
│   ├── 02_survival_analysis.ipynb
│   ├── 03_sbg_retention.ipynb
│   └── 04_cohort_analysis.ipynb
│
└── README.md
```

```text
kkbox-survival-retention-analysis/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_data_understanding_and_cleaning.ipynb
│   ├── 02_cohort_analysis.ipynb
│   ├── 03_survival_analysis_kaplan_meier.ipynb
│   ├── 04_cox_proportional_hazards.ipynb
│   └── 05_retention_forecasting_sBG.ipynb
│
├── src/
│   ├── data_prep.py
│   ├── cohort.py
│   ├── survival.py
│   └── forecasting.py
│
├── figures/
│
├── README.md
├── requirements.txt
└── walkthrough.md
```
