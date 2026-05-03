# Superstore Sales Intelligence — Executive Analysis

> Turning 4 years of raw retail transactions into actionable business strategy.  
> Revenue trends · Customer segmentation · RFM scoring · Regional performance

---

## Overview

This project analyzes **9,800 transactional records** from a retail superstore (2015–2018) to answer four business questions that come up in virtually every data engagement:

- Is the business actually healthy, or is revenue growth hiding a deeper problem?
- Which customers are driving value — and which are about to churn?
- Where are the highest-leverage growth opportunities?
- What operational signals (fulfillment, regional gaps) deserve immediate attention?

The full methodology, code, and narrative are in the notebook. The executive summary below covers the key findings.

---

## Key Findings

| # | Finding | Implication |
|---|---------|-------------|
| 1 | Revenue grew **54%** (2015→2018), but AOV fell **12%** — from $521 to $458 | Growth is volume-driven, not value-driven. Upsell and bundling strategies needed. |
| 2 | **197 Champions** (25% of customers) generate **41% of total revenue** ($1.0M) | Retention program for this cohort protects a disproportionate share of revenue. |
| 3 | **186 Potential customers** sit just below the Loyal threshold | Highest-leverage re-engagement target — low acquisition cost, high upside. |
| 4 | South region generates **$316K less** than West despite comparable size | Structural gap requiring competitive and distribution audit before expansion. |

---

## Dataset

| Field | Detail |
|-------|--------|
| Source | [Kaggle — Sample Superstore](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) |
| Rows | 9,800 transactions |
| Period | January 2015 – December 2018 |
| Fields | Order ID, Customer, Segment, Region, Category, Sub-Category, Sales |

> **Note on data quality:** The `Sales` column uses a non-standard decimal format (e.g. `9.575.775` instead of `9575.775`). A custom parser was written to handle this — see Section 3 of the notebook.

---

## Methodology

### 1. Revenue & Trend Analysis
Monthly aggregation with 3-month rolling average to separate signal from noise. YoY growth calculated against prior-year totals. AOV tracked independently from revenue to detect the volume-vs-value dynamic.

### 2. Customer Segmentation (RFM)
Customers scored on three dimensions using **quantile bins (1–4)**:

- **R — Recency:** days since last order (lower = higher score)
- **F — Frequency:** number of distinct orders (higher = higher score)  
- **M — Monetary:** total spend (higher = higher score)

Quantile bins were chosen over fixed thresholds to guarantee balanced segment sizes regardless of distribution skew — which is almost always present in retail data. Scores summed to a 3–12 range and mapped to five segments: Champions, Loyal, Potential, At Risk, Lost.

### 3. Regional & Category Analysis
Revenue, order count, and customer count broken down by region and product category. Sub-category ranked bar to identify product concentration risk.

### 4. Fulfillment Analysis
Lead time (order → ship) distribution by Ship Mode to assess whether service tiers are actually differentiated in practice.

---

## Results

```
Total Revenue (4Y):    $2,423,206
Total Orders:              4,922
Unique Customers:            793
Revenue CAGR:             15.5%

AOV change 2015→2018:    -$63 (-12%)

Champions:    197 customers  →  $1.00M  (41.4% of revenue)
Loyal:        216 customers  →  $831K
Potential:    186 customers  →  $407K
At Risk:      139 customers  →  $157K
Lost:          55 customers  →   $25K
```

---

## Project Structure

```
superstore-sales-intelligence/
│
├── superstore_analysis.ipynb   # Full analysis — EDA, RFM, charts, narrative
├── base_teste.csv              # Source dataset
├── report/
│   └── executive_report.html  # Standalone HTML report (open in browser)
└── README.md
```

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/ariellelages7/superstore-sales-intelligence.git
cd superstore-sales-intelligence

# Install dependencies
pip install pandas numpy matplotlib seaborn

# Launch the notebook
jupyter notebook superstore_analysis.ipynb
```

Or view the rendered notebook directly on [NBViewer](https://nbviewer.org/) — paste the repository URL.

---

## Tools & Stack

![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=flat&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-2.0-150458?style=flat&logo=pandas&logoColor=white)
![matplotlib](https://img.shields.io/badge/matplotlib-3.7-11557c?style=flat)
![seaborn](https://img.shields.io/badge/seaborn-0.12-4c72b0?style=flat)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)

---

## About

This project is part of my data analytics portfolio. I specialize in helping SaaS and product teams turn raw data into clear insights, dashboards, and business recommendations.

**Areas:** Product analytics · KPI tracking · Customer segmentation · Cohort analysis · Dashboard reporting

[LinkedIn](https://linkedin.com/in/arielle-lages) · [Upwork](https://upwork.com/freelancers/~01d57a3a01eb584140)
