# Hybrid Work & Employee Wellbeing Analytics

**Subtitle:** Impact of Work Modality on Sick Leave Rates in an Engineering Firm  
**Author:** Seyi Oladapo  
**Role:** Head, Human Resources — Anonymized Engineering Firm  
**Programme:** LBA – EMBA (UA High)

---

## Overview

This capstone investigates whether the engineering firm's hybrid work policy (introduced October 2024) materially reduced employee sick leave rates — a key signal for improved work-life balance and workforce availability. The analysis uses 114 monthly sick leave records spanning three policy periods: Pre-Hybrid, Hybrid, and Post-Hybrid.

---

## Business Question

> Did the October 2024 hybrid work policy reduce sick leave rates, and — after controlling for department and headcount — how much of the variation in sick leave can be attributed to work modality?

---

## Data

| Item | Detail |
|---|---|
| File | `data/hybrid_work_sick_leave_report_top_tech.csv` |
| Records | 114 monthly observations |
| Period | January 2023 – April 2026 |
| Policy phases | Pre-Hybrid (before Oct 2024) · Hybrid (Oct 2024 – Jan 2026) · Post-Hybrid |
| Key variables | `date`, `department`, `work_mode`, `sick_days`, `headcount_month`, `sick_leave_rate` |
| Source | Internal HRIS extract prepared for academic analysis |

> **Privacy:** The `Employee_Name` column is removed at the data-loading stage and does not appear anywhere in the analysis or published output.

---

## Analytical Techniques

1. **Exploratory Data Analysis** — distribution of sick leave rates by period and department; outlier detection; verification of assumptions for ANOVA and regression
2. **Data Visualisation** — monthly time-series with Hybrid window shaded; department-level breakdown charts; boxplots by period
3. **Hypothesis Testing** — one-way ANOVA across three policy periods; Tukey HSD pairwise comparisons (Pre-Hybrid vs Hybrid is the primary comparison); Kruskal-Wallis non-parametric robustness check; ANOVA and pairwise tests by department
4. **Correlation Analysis** — Pearson/Spearman correlations between structural covariates (headcount, department, period) and sick leave rate; multicollinearity screening before regression
5. **Multiple Regression (OLS)** — `sick_leave_rate` regressed on `period`, `department`, and `headcount_month` simultaneously; Hybrid-period coefficient is the primary policy estimate after controlling for confounders

---

## Key Findings

1. Sick leave behaviour differs by policy period; the Hybrid window shows a distinct pattern relative to the Pre-Hybrid baseline.
2. Departmental variation is significant — the policy effect is not uniform across teams.
3. Multivariate modelling confirms that period and workforce-structure variables jointly explain a meaningful share of sick leave variation.

---

## Recommendation

Maintain a refined hybrid policy with department-specific controls and quarterly sick leave monitoring. Extend the post-hybrid observation window before final policy lock-in, and collect a workload intensity indicator to address potential omitted-variable bias in future modelling cycles.

---

## Project Structure

```
seyi_capstone.qmd          # Quarto source (R + Python dual implementation)
seyi_capstone.html         # Rendered output
requirements.txt           # Python dependencies
data/
  hybrid_work_sick_leave_report_top_tech.csv
docs/
  cs_dara_review_score.md
  smry_captsone_brkdown.md
```

---

## Reproducing the Analysis

### R packages

Install from CRAN: `readr`, `dplyr`, `tidyr`, `tibble`, `purrr`, `forcats`, `ggplot2`, `lubridate`, `scales`, `ggcorrplot`, `patchwork`, `broom`, `knitr`, `kableExtra`, `e1071`, `janitor`

### Python packages

```bash
pip install -r requirements.txt
```

Packages: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`, `scikit-learn`, `shap`, `openpyxl`

### Render

```bash
quarto render seyi_capstone.qmd
```
