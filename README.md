# 🎯 Objectives  
## Developmental Screening Disparities & Predictive Modeling (NSCH 2022)

Early childhood developmental screening is a critical first step in identifying delays and connecting children to early intervention services.

This project aims to:

- Estimate the rate of developmental screening among children ages 0–3  
- Identify socioeconomic and demographic disparities in screening  
- Analyze the relationship between healthcare access and screening likelihood  
- Develop a baseline predictive classification model  
- Translate findings into actionable public health insights  

**Data task definition:**  
Using nationally representative child-level data from the 2022 National Survey of Children’s Health (NSCH), build and evaluate a baseline classification model (Logistic Regression) to predict whether a child received a developmental screening questionnaire and identify key disparity drivers.

---

# 🔍 CRISP-DM Summary

## 1. Business Understanding

Developmental delays affect long-term educational, health, and economic outcomes. Early screening improves early detection and intervention.

However, screening is not universal. Policymakers and early childhood leaders need data-driven insight into:

- Which children are less likely to be screened  
- How socioeconomic and racial disparities manifest  
- Which structural factors (e.g., preventive care access) influence screening  

This analysis provides an evidence-based foundation for targeted outreach and equitable intervention strategies.

---

## 2. Data Understanding

The dataset comes from the **2022 National Survey of Children’s Health (NSCH)**, a nationally representative survey conducted by the U.S. Census Bureau.

The dataset includes:

- Child demographics (age, race, ethnicity)  
- Household socioeconomic indicators (Federal Poverty Level)  
- Healthcare access variables (usual source of preventive care)  
- Developmental screening questionnaire items  

The target variable is derived from:

**k6q12 — “Questionnaire – Development Concerns”**

- 1 = Screening completed  
- 0 = Screening not completed  

The analysis is restricted to children ages 0–3.

After filtering and cleaning:
- Sample size ≈ 10,800 observations  
- Screening rate ≈ 45–46%  

---

## 3. Data Preparation

Key preparation steps included:

- Creating binary target variable `DEV_SCREEN`  
- Filtering dataset to children ages 0–3  
- Removing missing outcome values  
- Constructing Federal Poverty Level (FPL) percentage from six imputed variables  
- Binning FPL into interpretable income groups  
- Combining race and Hispanic ethnicity into a unified Race/Ethnicity variable  
- Applying official NSCH label definitions for categorical variables  

These steps ensured interpretability and model readiness.

---

## 4. Exploratory Data Analysis (EDA)

Visual analysis revealed:

- Developmental screening occurs in fewer than half of children ages 0–3  
- A strong socioeconomic gradient exists — screening increases with income  
- Racial and ethnic disparities are present  
- Children with a usual source of preventive care have significantly higher screening rates  

These findings suggest that both structural access and socioeconomic disadvantage influence screening likelihood.

### Visualizations

Target distribution:  
`images/dev_screen_distribution_0_3.png`

Screening by FPL:  
`images/screen_rate_by_fpl.png`

Screening by Race/Ethnicity:  
`images/screen_rate_by_race_ethnicity.png`

Screening by Usual Preventive Care:  
`images/screen_rate_by_usual_preventive_care.png`

---

## 5. Modeling

A **Logistic Regression** classifier was used as a baseline model due to:

- Interpretability  
- Suitability for binary classification  
- Ability to estimate probability of screening  

Features included:

- Federal Poverty Level (continuous)  
- Race/Ethnicity  
- Hispanic origin  
- Usual preventive care access  

Because the outcome is moderately imbalanced (~45% positive), **ROC-AUC** was selected as the primary evaluation metric.

The baseline model demonstrated meaningful predictive signal, indicating that socioeconomic and healthcare access variables contain substantial information about screening status.

---

## 6. Evaluation

Key observations:

- Screening rates are not evenly distributed across socioeconomic groups  
- Income gradient is pronounced and consistent  
- Preventive care access shows strong association with screening  
- Logistic Regression provides interpretable baseline discrimination  

Model evaluation emphasized:

- ROC-AUC  
- Precision  
- Recall  
- Confusion matrix  

Accuracy alone was not used as the primary metric.

---

## 7. Deployment & Public Health Insights

### Policy Interpretation

- Children from lower-income households are less likely to receive screening  
- Racial and ethnic disparities persist  
- Having a usual source of preventive care is strongly associated with screening  

### Recommendations

- Expand outreach in lower-income communities  
- Strengthen well-child visit access  
- Support culturally responsive engagement strategies  
- Use predictive modeling to identify high-risk subgroups for targeted intervention  

Future modeling (Module 24) will include:

- Tree-based ensemble models  
- Hyperparameter tuning  
- Potential incorporation of survey weights  
- Expanded feature sets  

---

# 📈 Tools & Libraries Used

- Python  
- Jupyter Notebook  
- pandas, numpy  
- seaborn, matplotlib  
- scikit-learn (LogisticRegression, train_test_split, ROC-AUC evaluation)  

---

# 📎 Notes

The NSCH 2022 Public Use File is not included in this repository due to size restrictions. It can be downloaded directly from the U.S. Census Bureau NSCH website.

## 📓 Notebook
- Main analysis notebook: `notebook/Capstone1.2.ipynb`


---

# 👩‍💻 Author  

**Annette Angel**  
UC Berkeley Professional Certificate in Machine Learning & Artificial Intelligence  
