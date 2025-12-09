

# **Task-4: Statistical Modeling & Predictive Analytics — ACIS Insurance**

## **1. Overview**

Task-4 focuses on building statistical and machine-learning models to help **ACIS Insurance** predict claim severity, understand the drivers of risk, and support the development of a **risk-adjusted premium system**.
Using the cleaned and version-controlled dataset, we implemented regression models, evaluated performance using cross-validation, and interpreted feature importance using SHAP values to reveal actionable insights.

This task builds on Week-3’s tasks in Git/GitHub, DVC, hypothesis testing, and data engineering.

---

## **2. Objectives**

The main goals of Task-4 were to:

* Build predictive models for **Total Claims** and **Total Premium**.
* Engineer features and preprocess data for optimal model accuracy.
* Evaluate different algorithms (Linear Regression, Random Forest, XGBoost).
* Interpret predictions using SHAP for business-level insights.
* Provide recommendations for **pricing**, **risk segmentation**, and **product optimization**.

---

## **3. Workflow Summary**

### **3.1 Data Preprocessing**

* Handled missing values using median/mode imputation.
* Encoded categorical variables (One-Hot Encoding).
* Processed date columns (extracting year, month, day).
* Split data into train/test sets using 80/20.
* Standardized or normalized numerical features where needed.

### **3.2 Modeling Algorithms**

Three main regression models were trained:

| Model                       | Purpose                    | Notes                                      |
| --------------------------- | -------------------------- | ------------------------------------------ |
| **Linear Regression**       | Baseline model             | Simple, interpretable                      |
| **Random Forest Regressor** | Nonlinear patterns         | High performance, handles mixed data types |
| **XGBoost Regressor**       | Advanced gradient boosting | Best for large and complex datasets        |

### **3.3 Evaluation Metrics**

Models were evaluated using:

* **RMSE (Root Mean Squared Error)**
* **MAE (Mean Absolute Error)**
* **R² Score**
* **5-Fold Cross-Validation** for reliability

### **3.4 Model Interpretation**

Using **SHAP (SHapley Additive exPlanations)**, we identified:

* High-risk drivers
* Most influential policyholder characteristics
* Factors that increase predicted claim amounts

---

## **4. Results Summary**

### **4.1 Best Performing Model**

The **Random Forest** or **XGBoost** model (depending on tuning) performed best with:

* Lower RMSE
* Better generalization
* More stable feature importance

### **4.2 Key Predictors of Claim Severity**

From SHAP and model analysis:

* **Vehicle Age** — older vehicles → higher expected claim costs
* **Province / Zip Code** — demographic and regional risk differences
* **Gender** — slight but statistically significant variation
* **Annual Premium Paid** — correlated with financial exposure
* **Make/Model** — certain models show higher average repair costs

### **4.3 Business Insights**

* Provinces with consistently high predicted claims should receive **adjusted pricing**.
* Vehicle type and age materially influence risk → opportunity for **age-based pricing tiers**.
* Low-risk customer segments can be incentivized through **discount programs**.

---


---




Just tell me!
