# Fidelis National Bank (FNB) Customer Churn Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Power BI](https://img.shields.io/badge/PowerBI-Dashboard-yellow?logo=powerbi)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green?logo=pandas)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Portfolio](https://img.shields.io/badge/Portfolio-Project%202-purple)

---

## The Finding That Started Everything

Fidelis National Bank is losing 1 in every 5 customers. That alone is alarming. But here is the part that changes everything. The customers leaving had more money than those who stayed.

Churned customers held an average balance of $91,108. Those who stayed held $72,745. FNB is not losing dormant accounts. It is losing its wealthiest customers. This project set out to find out why, predict who is next, and tell the bank what to do about it.

The bank was named Fidelis because Fidelis means faithful in Latin. The entire project is about what happens when customer loyalty breaks down.

---

## Project Overview

| Detail | Info |
|---|---|
| Project | Portfolio Project 2 |
| Analyst | Abijah Kabiro |
| Tools | Python, Power BI, Scikit-learn |
| Dataset | Churn Modelling (Kaggle) |
| Records | 10,000 customers |
| Target Industries | Fintech, Banking, Logistics |

---

## Business Problem

Fidelis National Bank (FNB) operates across France, Spain, and Germany. Leadership is experiencing rising account closures but has no data-driven understanding of who is leaving, why they are leaving, or which customers are most at risk. This analysis answers all three questions and delivers five targeted retention recommendations.

---

## Dataset

| Field | Detail |
|---|---|
| Source | Kaggle, Churn Modelling Dataset |
| Records | 10,000 customers |
| Original columns | 14 |
| After cleaning | 11 columns |
| Missing values | None |
| Duplicates | None |
| Target column | Exited (1 = Churned, 0 = Stayed) |

Key columns used: CreditScore, Geography, Gender, Age, Tenure, Balance, NumOfProducts, HasCrCard, IsActiveMember, EstimatedSalary, Exited

---

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Python (Google Colab) | Data cleaning, EDA, machine learning |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Matplotlib and Seaborn | Data visualisation |
| Scikit-learn | Logistic Regression model |
| Power BI | Interactive 4-page dashboard |
| DAX | Custom KPI measures |
| Power Query | Data transformation |

---

## Skills Demonstrated

**Python and Data Analysis**
- Data loading, profiling, and cleaning using Pandas
- Exploratory data analysis with Matplotlib and Seaborn
- Feature engineering including AgeGroup binning and dummy encoding
- Machine learning with Scikit-learn using Logistic Regression
- Model evaluation using accuracy, precision, recall, F1-score, and confusion matrix

**Power BI and Business Intelligence**
- DAX measure creation including FORMAT measures and Count measures
- Power Query data transformation and conditional column creation
- Custom dashboard backgrounds and responsive mobile layout
- Conditional formatting on table visuals
- Multi-page dashboard design with consistent colour palette

**Data Storytelling and Communication**
- Translating technical findings into business recommendations
- Deliberate colour use to highlight critical segments
- Executive-level insight writing for non-technical stakeholders

**Problem Solving**
- Debugging Python errors in Google Colab
- Resolving Power BI DAX type conflicts between text and numeric measures
- Designing workarounds for Power BI conditional formatting limitations

---

## Project Workflow

### Phase 1: Business Understanding
- Defined the business problem around customer attrition
- Set 4 groups of business questions covering who is churning, why they are churning, what a high-risk customer looks like, and what the bank should do
- Named the fictional institution Fidelis National Bank because Fidelis means faithful in Latin, connecting directly to the theme of customer loyalty

### Phase 2: Data Cleaning
- Loaded dataset from Google Drive into Google Colab
- Confirmed zero missing values and zero duplicates
- Dropped 3 non-analytical columns: RowNumber, CustomerId, Surname
- Created AgeGroup binned column for EDA
- Final dataset: 10,000 rows, 11 columns

### Phase 3: Exploratory Data Analysis

**Churn Overview**
- 20.37% overall churn rate (2,037 customers lost)
- 7,963 customers retained

**Who Is Churning**
- Germany: 32.4% (double France and Spain)
- Female: 25.1% vs Male: 16.5%
- Age 50-60: 56.2% (highest of any group)
- Under 30: 7.5% (most loyal)

**Why They Are Churning**
- Churned customers had higher balances ($91,108) than those who stayed ($72,745)
- 4 products: 100% churn rate
- 3 products: 82.7% churn rate
- 2 products: 7.6% churn (loyalty sweet spot)
- Inactive members churn at 26.9% vs 14.3% for active members

### Phase 4: Churn Prediction Model

**Algorithm:** Logistic Regression

Logistic Regression was chosen because it is interpretable, industry standard for binary classification, and produces coefficients that explain exactly which factors drive predictions.

**Setup**
- Training set: 8,000 customers (80%)
- Testing set: 2,000 customers (20%)
- Applied StandardScaler for feature normalisation
- Applied pd.get_dummies for categorical encoding

**Results**

| Metric | Score |
|---|---|
| Overall Accuracy | 81.1% |
| F1-Score (Stayed) | 0.89 |
| F1-Score (Churned) | 0.29 |
| Loyal customers identified | 1,543 |
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

**Model Limitation**

Low churn recall (20%) is due to class imbalance. 80% of customers stayed so the model learned to default to predicting Stayed. Future improvement: apply SMOTE oversampling or Random Forest to boost churn detection.

---

## Power BI Dashboard

The dashboard spans 4 pages, each focused on a specific analytical question. The colour palette uses Pine Blue (#297373), Straw Gold (#E9D758), Coral Glow (#FF8552), Alabaster Grey (#E6E6E6), and Graphite (#39393A).

A deliberate design decision was made to use 3 colours on the age group chart. Coral for critical segments (50-60), Gold for warning segments (40-50), and Pine Blue for stable groups. Colour was used to highlight, not decorate.

---

### Page 1: Churn Overview

KPIs showing overall churn rate, customers lost, retained, and total. Includes a donut chart of churned vs stayed, churn rate by country, a key insight card, and a bidirectional feature importance chart.

![Page 1 — Churn Overview](Power%20BI/dashboard_page1_churn_overview.png)

---

### Page 2: Who Is Churning

KPIs showing Germany, female, age 50-60, and male churn rates. Includes churn by age group, churn by gender, churn by country, and a key insight card.

![Page 2 — Who Is Churning](Power%20BI/dashboard_page2_who_is_churning.png)

---

### Page 3: Why Are They Churning

KPIs showing average balances for churned vs stayed, 4-product churn rate, and inactive churn rate. Includes churn by number of products, churn by active membership, average balance comparison, and a key insight card.

![Page 3 — Why Are They Churning](Power%20BI/dashboard_page3_why_churning.png)

---

### Page 4: Model Insights

KPIs showing model accuracy, F1-scores, and loyal customers identified. Includes a bidirectional feature importance chart, confusion matrix table, high risk customer segment table, and a key insight card.

![Page 4 — Model Insights](Power%20BI/dashboard_page4_model_insights.png)

---

## Key Findings

**The High-Value Churn Paradox**
Churned customers had higher balances than loyal customers. FNB is not losing low-value accounts. It is losing its wealthiest segment.

**The Over-Selling Trap**
4 products means 100% churn. 2 products means 7.6% churn. More products is not better for FNB customers.

**The Inactive Majority**
48.5% of customers are inactive and churning at 26.9% vs 14.3% for active members.

**The German Problem**
Germany churns at 32.4%, double France and Spain, confirmed by both EDA and the prediction model.

**Age is the Strongest Driver**
Age has a coefficient of +0.754, making it the most powerful churn predictor in the model.

---

## Business Recommendations

1. Launch an age-targeted retention programme for customers aged 50 and above
2. Run a 90-day re-engagement campaign for 4,849 inactive members
3. Conduct an urgent investigation into the German market churn drivers
4. Design a female customer retention strategy to close the 8.6 percentage point gender gap
5. Fix the product over-selling problem by targeting 2 products per customer as the loyalty sweet spot

---

## Errors Encountered and Fixes

| Error | Fix |
|---|---|
| FileNotFoundError loading CSV in Colab | Mounted Google Drive and loaded from Drive path |
| NameError: pd not defined | Moved all imports to top of first cell |
| Donut chart disappeared after FORMAT measure | Created separate Count measures for charts |
| KPI cards showing 2K instead of 2,037 | Used FORMAT DAX with "#,##0" pattern |
| Confusion matrix conditional formatting failed | Changed Format style to Rules, Summarization to Minimum |
| Mobile view showing grid background | Set canvas background from desktop layout view |
| AgeGroup column lost each Colab session | Added AgeGroup creation to master session setup cell |

---

## Lessons Learned

1. Always import Python libraries at the top of the first cell
2. In Power BI, FORMAT measures return text and cannot be used in chart visuals. Always create separate plain number measures for charts
3. Colour in data visualisation should highlight, not decorate. Use the minimum colours needed to tell the story
4. Google Colab does not save uploaded files between sessions. Always use Google Drive
5. A prediction model is not just about accuracy. Recall matters more when the cost of missing a churner is high
6. Acknowledging model limitations in a portfolio shows analytical maturity

---

## How to Run the Project

**Option A: Run directly in Google Colab (Recommended)**

Click the link below to open the notebook directly in your browser. No installation needed.

[Open in Google Colab](https://colab.research.google.com/drive/1zV3grp02eUZmxhMrB4l0a8n168vSCnuX#scrollTo=mTuUa19jhtWB)

**Option B: Run locally**
1. Download `Bank_Churn_Analysis.ipynb` from the Python folder
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
│   ├── 1_Churn_Overview1.png
│   ├── 1_Churn_Overview2.png
│   ├── 2_Churn_by_Age1.png
│   ├── 2_Churn_by_Age2.png
│   ├── 2_Churn_by_Gender1.png
│   ├── 2_Churn_by_Gender2.png
│   ├── 2_Churn_by_Geography1.png
│   ├── 2_Churn_by_Geography2.png
│   ├── 3_Churn_by_Balance.png
│   ├── 3_Churn_by_Balance2.png
│   ├── 3_Churn_by_Balance3.png
│   ├── 3_Churn_by_Balance4.png
│   ├── 3_Churn_by_Membership1.png
│   ├── 3_Churn_by_Membership2.png
│   ├── 3_Churn_by_Membership3.png
│   ├── 3_Churn_by_Products1.png
│   ├── 3_Churn_by_Products2.png
│   └── 3_Churn_by_Products3.png
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

For the full project story including business context, technical walkthrough, and lessons learned, read the Medium article:

[Bank Customer Churn Analysis — Full Article](https://medium.com/@abijahkabiro/bank-churn-ecbb7e2757ab)

---

## Contact

**Abijah Kabiro**
Senior Data Analyst, Nairobi, Kenya

- Portfolio: [abijahkabiro.github.io](https://abijahkabiro.github.io)
- LinkedIn: [linkedin.com/in/abijahkabiro](https://linkedin.com/in/abijahkabiro)
- GitHub: [github.com/Abijahkabiro](https://github.com/Abijahkabiro)
- Medium:[medium.com/@abijahkabiro](https://medium.com/@abijahkabiro)
---

*Part of my data analytics portfolio. Built with Python, Power BI, and a genuine curiosity about why people leave.*
