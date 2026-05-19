# Section A Template (30 Marks) - Seyi Oladapo

## 1) Executive Summary (10 marks)

### Business context
As Head of HR, I evaluate attendance and health-related absence patterns to inform workforce policy and productivity planning. During and after the hybrid work program, management needed evidence on whether hybrid arrangements reduced sick leave usage.

### Research question
Did sick leave usage materially reduce during the hybrid work period compared with pre-hybrid and post-hybrid periods?

### Three key findings (insert your final numbers)
1. [Average sick leave difference by period]
2. [Statistical significance result from hypothesis testing]
3. [Most important control variable effect from regression/correlation]

### One recommendation
[Hybrid-policy adjustment] should be maintained/refined for [specific departments], with expected reduction of [X%] in sick leave rate.

## 2) Professional Disclosure (10 marks)

**Job title:** Head, Human Resources
**Organisation:** Toptech Engineering Limited — a Nigerian engineering services company

### Technique 1 — Exploratory Data Analysis
As Head of HR at Toptech Engineering, I track workforce metrics including attendance, leave utilization, and department headcount monthly. Before drawing any policy conclusion about hybrid work's effect on sick leave, I need to understand the baseline distribution of the 114 records in the dataset. EDA will answer: Is sick leave usage evenly distributed across departments or concentrated in specific teams? Are there extreme outlier months or events that distort the overall average? Is the `Sick_Leave_Rate` distribution approximately normal or heavily skewed? These baseline findings directly shape which statistical tests are appropriate and how I will present the story to the executive team. This step replicates the monthly HR metrics review I conduct before any workforce policy proposal goes to management.

**Alternative considered:** Proceeding directly to a t-test or ANOVA comparing periods without first profiling the data. Rejected because undetected outliers (e.g., a single month with a mass sick-leave event during a flu outbreak) would bias the period-level comparison and lead to incorrect conclusions.

**Limitation:** EDA is descriptive and cannot establish statistical significance. A visually obvious difference between hybrid and non-hybrid months must still be validated by a formal hypothesis test.

### Technique 2 — Data Visualization
HR policy recommendations at Toptech are presented to the CEO and executive committee in visual format. The most compelling argument for or against a hybrid work policy will not be a table of averages — it will be a time series chart showing monthly sick leave rate from January 2023 to April 2026, with clear period annotations marking the hybrid start (October 2024) and end (January 2026). Box plots comparing sick leave distributions across the three periods (pre-hybrid, hybrid, post-hybrid) and across departments will allow the executive team to see the pattern immediately. These visualizations will form the centrepiece of any formal hybrid work proposal I present.

**Alternative considered:** Presenting findings through written summary statistics only. Rejected because the management audience at Toptech expects and responds to visual data, and a chart communicates the temporal pattern far more efficiently than a paragraph.

**Limitation:** Visual comparisons can appear more decisive than they are. The apparent difference between periods in a chart could be driven by seasonal illness patterns rather than the work mode change. All visualizations are paired with formal tests.

### Technique 3 — Hypothesis Testing
The core business question — "Did hybrid work reduce sick leave usage?" — is precisely a hypothesis test. I need to formally compare `Sick_Leave_Rate` across the three periods (pre-hybrid: January 2023–September 2024; hybrid: October 2024–January 2026; post-hybrid: February 2026–April 2026) using a one-way ANOVA or Welch t-test and report the p-value and effect size (Cohen's d or eta-squared). Without a formal test, the difference I observe in the charts is anecdotal. A statistically significant result gives me a defensible, evidence-based case to present a formal hybrid work proposal to the board — replacing the current head-knowledge argument with a p-value.

**Alternative considered:** Presenting only descriptive period-level averages without formal testing. Rejected because management decisions based on descriptive comparisons are vulnerable to challenge and do not satisfy the evidence standard required for a policy reversal.

**Limitation:** With 114 records split across three periods, the post-hybrid period (February–April 2026, approximately 3 months) has the fewest observations and the lowest statistical power. Post-hybrid conclusions will be explicitly qualified as preliminary pending a longer post-hybrid data window.

### Technique 4 — Correlation Analysis
Sick leave usage is unlikely to be driven by work mode alone. `Department`, `Headcount_Month`, and `Day_of_Week` are plausible covariates. Correlation analysis maps these associations formally before I build the regression model. Specifically, I need to know: Does department size (Headcount_Month) correlate with sick leave rate — because larger teams may have better leave coverage and more recorded absences? Are certain departments correlated with higher leave rates independently of work mode? These relationships determine which control variables must be included in the regression to isolate the hybrid effect.

**Alternative considered:** Including all available variables in the regression without prior correlation screening. Rejected because some variables (e.g., `Month` and `Headcount_Month`) may be collinear in ways that distort the regression coefficients and inflate standard errors.

**Limitation:** Correlation identifies linear association only. Non-linear effects — for example, a threshold department size below which sick leave spikes — will not be captured by a correlation coefficient.

### Technique 5 — Multiple Regression
A regression model with `Sick_Leave_Rate` as the outcome and `Work_Mode`, `Department`, `Headcount_Month`, and a month-number trend variable as predictors allows me to isolate the independent effect of hybrid working on sick leave, controlling for team size, functional differences, and any underlying time trend. The coefficient on `Work_Mode` will form the quantitative core of any future hybrid work policy proposal I submit to the board: "Controlling for department size and composition, hybrid working was associated with a [X percentage point] reduction in monthly sick leave rate, a difference that is statistically significant at p = [value]."

**Alternative considered:** An unadjusted mean comparison of sick leave across periods. Rejected because this approach cannot separate the effect of work mode from confounding factors such as department composition changes, seasonal illness variation, or headcount fluctuations.

**Limitation:** The dataset has 114 records across 9 variables. The regression is adequately powered for 4–5 predictors but at the lower end. Results should be interpreted with caution and cross-validated with the hypothesis test results.

---

## 3) Data Collection & Sampling (10 marks)

- **Source:** Human Resource Information System (HRIS), Toptech Engineering Limited
- **Primary dataset:**
  - `hybrid_work_sick_leave_report_top_tech.csv` — 114 records; 9 variables: Employee_Name, Date, Month, Work_Mode, Sick_Days, Headcount_Month, Sick_Leave_Rate, Day_of_Week, Department
- **Collection method:** Data was extracted from the company's HRIS, which logs attendance and leave records for all employees. Records were compiled and structured by the Head of HR (the student) using internal reporting tools. A partial anonymization pass was applied before export. The dataset was prepared specifically for this academic exercise.
- **Period covered:** January 2023 – April 2026 (3 years and 4 months), spanning three distinct work-mode periods:
  - **Pre-hybrid baseline:** January 2023 – September 2024 (21 months)
  - **Hybrid period:** October 2024 – January 2026 (16 months)
  - **Post-hybrid period:** February 2026 – April 2026 (3 months)
- **Sample frame:** All employees at Toptech Engineering Limited with attendance and leave records in the HRIS during the period. [CONFIRM before submission: Do the 114 records represent individual leave events (one row per absence episode), or monthly department-level aggregates (one row per department per month)? This affects the statistical unit and the appropriate hypothesis test. State this clearly in the final document.]
- **Sample size:** 114 records, 9 variables. Meets the CS1 minimum of 100 observations and 6 variables. The three-period design is well-suited to a one-way ANOVA or repeated-measures comparison.
- **Statistical justification:** The pre-hybrid period (21 months) provides the strongest baseline for comparison. The hybrid period (16 months) provides adequate observations for a within-period comparison. The post-hybrid period (3 months) is short and results for this period will be explicitly qualified as preliminary. For regression with 4–5 predictors, the 10-per-predictor guideline requires at least 40–50 observations — met with 114 records. For ANOVA across three periods, each group has at least 30+ records (pre-hybrid is the longest), providing adequate power for detection of a medium-sized effect.
- **Ethical notes and confidentiality:** The `Employee_Name` field is present in the raw dataset but will be fully removed or replaced with anonymized identifiers before the public RPubs submission — the student has explicitly stated that employee names should not be published. No sensitive medical diagnostic information is included; the dataset records leave days only, not the underlying reason for absence at the individual level. [CONFIRM and insert: "Use of this dataset was approved by [Name, Title] at Toptech Engineering Limited for the purposes of this academic assessment at Lagos Business School."] The dataset is used exclusively for this academic exercise and will not be commercially distributed or shared outside the LBS programme.
