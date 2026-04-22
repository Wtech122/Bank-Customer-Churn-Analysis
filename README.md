<div align="center">

# Bank Customer Churn Analysis

**Identifying why 1 in 5 bank customers leave and what to do about it.**


</div>

---

## Table of Contents

- [Project Overview](#project-overview)
- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Visualization](#visualization)
- [Limitations & Future Work](#limitations--future-work)
- [License](#license)
- [Contact](#contact)


---

## Project Overview

This project analyses a dataset of 10,000 bank customers across France, Germany, and Spain to uncover the root causes of customer churn. Using exploratory data analysis, pivot table breakdowns, and financial modelling, the project identifies the highest-risk customer segments and translates the findings into seven actionable retention recommendations.

> **Key result:** The overall churn rate stands at **20.4%** — with Germany at **32.4%**, middle-aged customers (48–57) at **55.3%**, and 3–4 product holders at **82.7–100%** churn, representing the most critical at-risk groups.

---

## Business Problem

**Problem statement:** The bank is losing 1 in 5 customers, and the customers leaving tend to be among its most financially valuable — those with balances over $100,000 and those in their peak earning years. Without understanding *who* is leaving and *why*, targeted retention efforts are impossible.

**Objectives:**
- Identify the customer segments with the highest churn rates across demographics, geography, and financial behaviour
- Quantify the deposit value at risk from ongoing churn
- Deliver concrete, prioritised recommendations to reduce churn below 15% within 12 months

---

## Dataset

| Attribute | Details |
|-----------|---------|
| **Source** | Mavenanalytics — "Bank Customer Churn" |
| **Size** | 10,000 rows × 13 columns |
| **Geography** | France (5,014), Germany (2,509), Spain (2,477) |
| **Granularity** | Per customer |
| **License** | MIT |

**Key fields:**

| Column | Type | Description |
|--------|------|-------------|
| `CustomerId` | `int` | Unique customer identifier |
| `Surname` | `string` | Customer surname |
| `CreditScore` | `int` | Customer credit score (range: 350–850) |
| `Geography` | `string` | Country of residence (France, Germany, Spain) |
| `Gender` | `string` | Customer gender (Male / Female) |
| `Age` | `int` | Customer age (range: 18–92, mean: 38.9) |
| `Tenure` | `int` | Years with the bank (0–10) |
| `Balance` | `float` | Account balance in USD (mean: $76,486) |
| `NumOfProducts` | `int` | Number of bank products held (1–4) |
| `HasCrCard` | `binary` | Whether the customer holds a credit card (Yes/No) |
| `IsActiveMember` | `binary` | Whether the customer is an active member (Yes/No) |
| `EstimatedSalary` | `float` | Estimated annual salary (mean: $100,090) |
| `Exited` | `binary` | Target variable — whether the customer churned (Yes/No) |

> **Note:** The raw dataset (`Bank_Churn.csv`) contained no missing values. Cleaning steps focused on standardising data types, encoding categorical variables, and structuring the data for pivot analysis.

---

## Methodology

```
Raw Data (Bank_Churn.csv) → Cleaning & Preprocessing → EDA → Pivot Table Analysis → Dashboard → Insights & Recommendations
```

1. **Data Cleaning** — Verified zero missing values; sorted `CustomerId` in ascending order (Smallest to biggest); standardised data types; encoded binary columns (HasCrCard, IsActiveMember, Exited) as Yes/No labels for readability
2. **Exploratory Data Analysis (EDA)** — Computed distributions, churn rates, and cross-tabulations across all key dimensions: country, gender, age group, balance tier, credit score band, product count, tenure, and activity status
3. **Pivot Table Analysis** — Built 8 pivot tables in Excel covering: churn by tenure, churn by salary, churn by country & gender, churn by age group, churn by balance, churn by credit score, churn by products, and churn by credit card status
4. **KPI Dashboard** — Summarised top-line metrics including total customers (10,000), overall churn rate (20.4%), inactive members churn rate (36.48%), total deposit pool ($764.9M), and deposits lost to churn ($185.6M)
5. **Insights & Recommendations** — Translated all analytical findings into seven prioritised, actionable retention strategies with measurable targets

---

## Key Findings

- **Germany Losing Customers Fast** — Germany's churn rate is **32.4%**, nearly double France (16.2%) and Spain (16.7%). Nearly 1 in 3 German customers leaves.
- **Middle-Aged Customers (48–57) Are Highest-Risk** — Churn rate of **55.3%** in this age group — the bank's highest-value earning segment is its most likely to leave.
- **3–4 Product Holders Almost Always Leave** — Churn rates of **82.7%** (3 products) and **100%** (4 products) suggest product overload is a major churn trigger.
- **Low Credit Score Customers at Risk** — Churn rate of **33%** for the 350–449 credit score band vs. 19–20% for the 650–850 band. Risk profiles predict exit behaviour.
- **High Balance Customers Leaving** — **100% churn** for $250K–$300K balance holders and **54.6%** for $200K–$250K holders, threatening the $764.9M deposit pool.
- **Women Leave More Than Men** — Female churn rate is **25.1%** vs. **16.5%** for males — an 8.6 percentage-point gap that holds across all three countries.
- **Total Deposit Value at Risk** — Of the $764.9M total deposit base, **$185.6M** has already been lost to churned customers.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Microsoft Excel 2019+ | Pivot tables, KPI calculations, charts, dashboard |
| Power Query (Excel) | Data cleaning, Column type conversion, data transformation |
| Microsoft Word | Final analysis report and recommendations |

---

## Project Structure

```
bank-churn-analysis/
├── data/
│   ├── raw/
│   │   └── Bank_Churn.csv           # Original 10,000-row dataset (13 columns)
│   └── processed/
│       └── Churn_Analysis.xlsx               # Cleaned data + pivot tables + KPI dashboard
├── reports/
│   └── Churn_Rate_Report.docx              # Full analysis report with recommendations
└── README.md
└── LICENSE

```


---

## Visualization

The Excel dashboard contains 6 charts built from pivot data.


> Dashboard: <img width="1366" height="768" alt="Image" src="https://github.com/user-attachments/assets/fcfd6db2-510d-4d2c-ad5a-69425c5fecd5" />


---

## Limitations & Future Work

**Current limitations:**
- The dataset is a static snapshot; no time-series dimension is available to track churn evolution over months or quarters
- Causal claims cannot be made from this analysis alone — the patterns identified are correlational
- Estimated salary is an approximation, not verified income data
- No customer lifetime value (CLV) model has been applied to prioritise which churned segments are costliest

**Planned improvements:**
- [ ] Build a predictive churn model (logistic regression or gradient boosting) using the cleaned dataset
- [ ] Add CLV scoring to prioritise retention spend by financial impact
- [ ] Automate monthly churn reporting via a scheduled Python pipeline
- [ ] Deploy an interactive version of the dashboard in Power BI or Streamlit

## License

Distributed under the **MIT License**. This project is for educational and portfolio purposes.

---

## Contact


* **LinkedIn:** [al-ameen-lamina](https://www.linkedin.com/in/al-ameen-lamina/)
* **Email:** [laminaalameen2022@gmail.com](mailto:laminaalameen2022@gmail.com)



