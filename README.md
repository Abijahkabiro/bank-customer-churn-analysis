# Fidelis National Bank (FNB) Customer Churn Analysis

Identifying which customers are leaving, why they are leaving, and what the bank should do about it — using Python, Power BI, and a Logistic Regression prediction model.

**Author:** Abijah Kabiro | Data Analyst | Nairobi, Kenya
**Tools:** Python · Power BI · Scikit-learn · Pandas · NumPy · Matplotlib · Seaborn · DAX · Power Query
**Dataset:** [Churn Modelling Dataset (Kaggle)](https://www.kaggle.com/datasets/shrutimechlearn/churn-modelling) — 10,000 customers
**Project Type:** Customer Analytics · Churn Prediction · Retention Strategy

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Power BI](https://img.shields.io/badge/PowerBI-Dashboard-yellow?logo=powerbi)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green?logo=pandas)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)


---

## Business Context

Fidelis National Bank operates across France, Spain, and Germany. The bank is losing customers at a rate that should concern any leadership team. 1 in every 5 customers has left. But the more alarming finding is not the volume of customers leaving. It is who is leaving.

Churned customers held an average balance of $91,108. Customers who stayed held $72,745. FNB is not losing dormant, low-value accounts. It is losing its most financially engaged customers.

The goal of this project was not simply to report that churn exists. The goal was to find where the problem lives, understand why it is happening across different customer segments, predict which customers are at risk next, and give the bank a clear set of actions to respond.

The bank was named Fidelis because Fidelis means faithful in Latin. The entire project is about what happens when customer loyalty breaks down.

---

## Business Questions

The analysis was structured around four groups of questions, each answered through data:

**Group 1: Who is churning?**
- What is the overall churn rate?
- Which country has the highest churn?
- Does gender affect churn?
- Which age group churns the most?

**Group 2: Why are they churning?**
- Do churned customers have lower credit scores?
- Do inactive members churn more?
- Does account balance affect churn?
- Does number of products affect churn?
- Does length of time with the bank affect churn?

**Group 3: What does a high-risk customer look like?**
- What is the profile of a typical churned customer?
- Which combination of factors is most associated with churn?

**Group 4: What should the bank do?**
- Which customer segments need urgent retention action?
- What retention strategies should FNB prioritise?

---

## Project Approach

**Phase 1: Business Understanding**

Started by defining the churn problem and structuring the analysis around the four business question groups before writing any code. Documented the analytical objectives upfront so every chart and model output had a clear purpose tied to a business decision.

**Phase 2: Data Cleaning**

Ran profiling checks before touching the data. Confirmed zero missing values and zero duplicates. Removed three non-analytical columns (RowNumber, CustomerId, Surname) that carry no predictive value. Created an AgeGroup column to support demographic segmentation during EDA. Final dataset: 10,000 rows, 11 columns.

**Phase 3: Exploratory Data Analysis**

Analysed churn patterns across geography, gender, age, account balance, number of products held, membership activity, credit score, and tenure. Each analysis was built to answer a specific business question rather than simply describe the data.

**Phase 4: Churn Prediction Model**

Built a Logistic Regression model to predict which customers are most likely to churn. Logistic Regression was chosen because it is interpretable. Every coefficient can be explained to a business stakeholder, and the model output can directly inform retention prioritisation decisions.

**Phase 5: Dashboard**

Built a 4-page Power BI dashboard covering churn overview, customer profiling, behavioural drivers, and model insights. Designed for both desktop and mobile viewing.

---

## Key Findings

**1. FNB is losing its most valuable customers**

The expectation is that customers who leave are the less engaged, lower-balance accounts. The data says the opposite. Churned customers held $18,363 more on average than those who stayed. This is not a dormant account problem. It is a high-value customer retention failure.

**2. Germany is a structural problem, not a regional blip**

Germany's churn rate of 32.4% is double that of France (16.2%) and Spain (16.7%). This gap is consistent across the dataset and confirmed by the prediction model. Something specific to the German market is driving customers away at twice the rate of every other region. The fix is not operational. It requires a market-level investigation.

**3. The over-selling trap is real**

Customers holding 2 products churn at 7.6%, the lowest of any group. Customers with 3 products churn at 82.7%. Customers with 4 products have a 100% churn rate. Every single one has left. FNB's sales strategy is pushing too many products onto customers who do not want them, and the data shows it is actively driving the most engaged customers out the door.

**4. Age 50-60 is a crisis segment**

More than half of customers in the 50-60 age group have churned (56.2%). This is 35.8 percentage points above the overall average. Customers under 30 churn at just 7.5% and represent the most loyal segment in the portfolio. The bank's retention resources are not being directed at the customers who need them most.

**5. Nearly half the bank is inactive**

48.5% of FNB customers are inactive members. Inactive members churn at 26.9% compared to 14.3% for active members. This is not just a churn problem. It is an engagement crisis that the bank has not yet addressed.

**6. Tenure offers a small but meaningful buffer**

Customers who stayed had an average tenure of 5.1 years compared to 4.9 years for churned customers. The difference is small but the direction is clear. Longer relationships offer some protection against churn. Customers in their first year are the most vulnerable.

**7. The prediction model confirms age and engagement as the two strongest signals**

Age carries a coefficient of +0.754, the highest of any variable. Active membership carries -0.533, the strongest protective factor. These two variables alone explain the most about who will leave. The model achieved 81.1% overall accuracy but struggled to catch churners specifically due to class imbalance, documented in the model section below.

---

## The High-Risk Customer Profile

Combining all findings from EDA and the prediction model, the typical churned FNB customer looks like this:

- Aged between 50 and 60
- Female
- Based in Germany
- Holds 3 or 4 bank products
- Inactive member
- Has been with the bank for less than 2 years
- Holds a higher than average account balance

This profile is the starting point for any targeted retention campaign. Customers matching three or more of these characteristics should be flagged for immediate outreach.

---

## Dashboard Preview

### Page 1: Churn Overview

KPIs showing overall churn rate, customers lost, customers retained, and total customers. Includes a donut chart of churned vs stayed, churn rate by country, a key insight card, and a bidirectional feature importance chart showing which factors increase and reduce churn.

![Page 1 — Churn Overview](Power%20BI/dashboard_page1_churn_overview.png)

---

### Page 2: Who Is Churning

KPIs showing Germany, female, age 50-60, and male churn rates. Includes churn by age group, churn by gender, churn by country, and a key insight card.

![Page 2 — Who Is Churning](Power%20BI/dashboard_page2_who_is_churning.png)

---

### Page 3: Why Are They Churning

KPIs showing average balances for churned vs stayed customers, 4-product churn rate, and inactive member churn rate. Includes churn by number of products, churn by active membership, average balance comparison, average tenure comparison, and a key insight card.

![Page 3 — Why Are They Churning](Power%20BI/dashboard_page3_why_churning.png)

---

### Page 4: Model Insights

KPIs showing model accuracy, F1-scores for churned and retained customers, and loyal customers correctly identified. Includes a bidirectional feature importance chart, confusion matrix, high risk customer segment table, and a key insight card.

![Page 4 — Model Insights](Power%20BI/dashboard_page4_model_insights.png)

---

## Model Results

| Metric | Score |
|---|---|
| Overall Accuracy | 81.1% |
| F1-Score (Stayed) | 0.89 |
| F1-Score (Churned) | 0.29 |
| Loyal customers correctly identified | 1,543 |
| Churners correctly caught | 79 out of 393 |
| Churners missed | 314 |

**Feature Importance**

| Feature | Coefficient | Direction |
|---|---|---|
| Age | +0.754 | Increases churn |
| IsActiveMember | -0.533 | Reduces churn |
| Geography Germany | +0.337 | Increases churn |
| Gender Male | -0.265 | Reduces churn |
| Balance | +0.161 | Increases churn |
| CreditScore | -0.068 | Reduces churn |
| NumOfProducts | -0.060 | Reduces churn |
| Tenure | -0.043 | Reduces churn |

Positive coefficients push customers toward leaving. Negative coefficients pull customers toward staying. Age is the single strongest driver. Active membership is the single strongest protector.

**Model Limitation**

The model correctly identified loyal customers at a high rate but only caught 20% of actual churners. This is a known consequence of class imbalance. 80% of customers stayed, so the model learned that predicting Stayed is the safer default. In a real banking context, missing a churner is far more costly than a false alarm. Future iterations should apply SMOTE oversampling or Random Forest to improve churn recall specifically.

Documenting this limitation matters. A model that catches 20% of churners is not a failure. It is a starting point that tells the bank exactly where to invest next.

---

## Business Recommendations

**1. Launch an age-targeted retention programme for customers aged 50 and above**
With a 56.2% churn rate, this segment is losing more than half its customers. Assign dedicated relationship managers, offer preferential rates, and run personalised outreach campaigns targeted at this group before more accounts close.

**2. Run a 90-day re-engagement campaign for inactive members**
4,849 customers are inactive and churning at nearly double the rate of active members. A structured re-engagement campaign using personalised communication, fee waivers, and mobile banking onboarding could recover a significant portion of these accounts before they are permanently lost.

**3. Investigate the German market urgently**
A 32.4% churn rate that is double every other market cannot be explained by normal variation. Something specific to Germany is driving this. Exit interviews with churned German customers and a competitor benchmarking exercise would identify the root cause and inform a market-specific response.

**4. Design a retention strategy for female customers**
Female customers churn at 25.1% compared to 16.5% for males, an 8.6 percentage point gap. This suggests the current product or service experience is not meeting the needs of this segment. A review of product fit and service touchpoints for female customers is a necessary first step.

**5. Stop over-selling products**
The data is clear. Two products is the loyalty sweet spot. Three or four products is where churn accelerates to dangerous levels. Audit the sales incentive structures that are rewarding product volume over customer fit and retrain relationship managers on needs-based selling.

---

## Errors Encountered and Fixes

Real projects hit real problems. These were the issues encountered and how they were resolved.

| Error | Cause | Fix |
|---|---|---|
| FileNotFoundError loading CSV in Colab | File uploaded locally, not to Drive | Mounted Google Drive and loaded from the Drive path |
| NameError: pd not defined | Library imports placed mid-notebook | Moved all imports to the top of the first cell |
| Donut chart disappeared after FORMAT measure | FORMAT returns text, which charts cannot use | Created separate plain COUNT measures for all chart visuals |
| KPI cards showing 2K instead of 2,037 | Power BI defaulting to abbreviated display | Used FORMAT DAX with the "#,##0" pattern to force exact numbers |
| Confusion matrix conditional formatting not applying | Summarization set to Sum instead of Minimum | Changed Format style to Rules and Summarization to Minimum |
| Mobile view showing grid background | Background set in mobile layout view has no effect | Set canvas background from desktop layout view before switching to mobile |
| AgeGroup column disappearing each session | Column created mid-session without saving to setup cell | Added AgeGroup creation to the master session setup cell |
| Feature importance chart showing all positive bars | ChurnDrivers table entered without negative values | Updated table with correct negative coefficients for protective features |

---

## Lessons Learned

1. Always import Python libraries at the top of the first cell. Running imports anywhere else causes session failures that are difficult to debug.

2. In Power BI, FORMAT measures return text and cannot be used in chart visuals. Always create two versions of each measure: one formatted for display in KPI cards, one plain numeric for use in charts.

3. Colour in data visualisation should highlight, not decorate. Three colours were used deliberately on the age group chart. Coral for critical (50-60), Gold for warning (40-50), Pine Blue for stable groups. The minimum number of colours needed to tell the story is always the right number.

4. Google Colab does not save uploaded files between sessions. Always connect to Google Drive and load from there.

5. Recall matters more than accuracy in churn prediction. A model that achieves 81% accuracy but misses 80% of churners is not doing the job the business needs it to do. Optimising for recall, not just accuracy, is the right priority for this problem.

6. Acknowledging model limitations openly is a sign of analytical maturity, not weakness. Every portfolio project should document what the model did not do well and why.

---

## How to Run the Project

**Option A: Run directly in Google Colab (Recommended)**

No installation needed. Click the link, sign in with your Google account, and run all cells from top to bottom.

[Open in Google Colab](https://colab.research.google.com/drive/1zV3grp02eUZmxhMrB4l0a8n168vSCnuX#scrollTo=mTuUa19jhtWB)

**Option B: Run locally**
1. Download `Bank_Churn_Analysis.ipynb` from the Python folder in this repository
2. Upload `Churn_Modelling.csv` to your Google Drive
3. Open the notebook in Google Colab
4. Update the file path in Cell 1 to match your Drive location
5. Run all cells in order from top to bottom

**Power BI Dashboard**
1. Download `FNB_Churn_Dashboard.pbix` from the Power BI folder
2. Open in Power BI Desktop
3. Navigate between pages using the tabs at the bottom

---

## File Structure

```
bank-customer-churn-analysis/
│
├── Churn_Modelling.csv
├── README.md
│
├── Python/
│   ├── Bank_Churn_Analysis.ipynb
│   └── (EDA charts)
│
└── Power BI/
    ├── FNB_Churn_Dashboard.pbix
    ├── dashboard_page1_churn_overview.png
    ├── dashboard_page2_who_is_churning.png
    ├── dashboard_page3_why_churning.png
    └── dashboard_page4_model_insights.png
```

---

## Further Reading

For the full project story including business context, technical walkthrough, errors encountered, and lessons learned, read the Medium article:

[Fidelis National Bank Customer Churn Analysis — Full Article](https://medium.com/@abijahkabiro/bank-churn-ecbb7e2757ab)

---

## About This Project

Built by **Abijah Kabiro**, a data analyst based in Nairobi, Kenya with four years of experience in supply chain, logistics, and customer analytics. This project was built to demonstrate how Python and Power BI can work together to move from raw customer data to actionable retention strategy, not just charts for visual effect.

**Connect:** [LinkedIn](https://linkedin.com/in/abijahkabiro) · [Portfolio](https://abijahkabiro.github.io) · [GitHub](https://github.com/Abijahkabiro) · [Medium](https://medium.com/@abijahkabiro)
