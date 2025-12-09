

## 📌 **Task 1 — Git, GitHub, EDA & Statistics**

### **1.1 Git and GitHub**

This project follows best practices for version control and collaborative analytics.

#### **What was done**

* Created GitHub repository for the challenge
* Added a clear project structure
* Setup Git version control workflow
* Created a new branch: `task-1`
* Performed frequent, descriptive commits
* Added a README and development documentation
* (Optional) Setup CI/CD workflow using GitHub Actions

#### **Key Skills Demonstrated**

* Git branching strategy
* Version control best practices
* CI/CD fundamentals
* Professional repository structure

---

### **1.2 Exploratory Data Analysis (EDA) & Statistical Understanding**

#### **Objectives**

Develop a foundational understanding of the dataset and extract actionable insights about risk, claims, and premium behavior.

#### **Work Completed**

### **✔ Data Understanding**

* Reviewed structure of 70+ columns: client, vehicle, location, plan, and claims
* Verified data types and converted to correct formats (datetime, categorical, numeric)

### **✔ Data Quality Assessment**

* Checked for missing values
* Identified inconsistencies and outliers
* Verified duplicate records

### **✔ Data Summarization**

* Generated descriptive statistics for:

  * `TotalPremium`
  * `TotalClaims`
  * `SumInsured`
  * `CustomValueEstimate`
  * Other numeric columns

### **✔ Univariate Analysis**

* Plotted:

  * Histograms (premium, claims, value estimates)
  * Bar charts for categorical features (Province, Gender, VehicleType)

### **✔ Bivariate & Multivariate Analysis**

* Explored correlations between:

  * TotalPremium vs TotalClaims
  * Claims behavior by ZipCode
  * Loss Ratio by Province, Gender, VehicleType

* Used:

  * Scatter plots
  * Box plots
  * Correlation matrices

### **✔ Outlier Detection**

* Box plots for extreme claim amounts
* Distribution analysis for high-value vehicles

### **✔ Required Visualizations**

Produced **3 insightful plots** highlighting:

1. Loss Ratio by Province
2. Distribution of Total Claims
3. Relationship between Premiums and Claims

---

---

# **Task 2 — Data Version Control (DVC)**

Establishing a **reproducible, auditable** data pipeline using DVC.

## 🎯 **Objectives**

Ensure that datasets and results can be precisely reproduced at any time — a critical requirement in insurance and finance.

---

## ✔ **Work Completed**

### **1. Installed DVC**

```bash
pip install dvc
```

### **2. Initialized DVC inside the project**

```bash
dvc init
```

### **3. Created Local Remote Storage**

```bash
mkdir dvc_remote_storage
dvc remote add -d local_remote dvc_remote_storage/
```

### **4. Tracked Data Using DVC**

```bash
dvc add <your_dataset.csv>
```

This generates a `.dvc` file linked to dataset metadata.

### **5. Committed DVC Files to Git**

```bash
git add .
git commit -m "Initialize DVC and track dataset"
```

### **6. Pushed Data to Local Remote**

```bash
dvc push
```

---

## ✔ **Task 2 Requirements Completed**

* Merged `task-1` into `main` via Pull Request
* Created `task-2` branch
* Installed & configured DVC
* Set up local remote storage
* Added dataset to DVC
* Committed `.dvc` files
* Pushed dataset to remote storage

---

## 📁 **Project Structure (Up to Task 2)**

```
├── data/
│   ├── raw/
│   │   └── insurance_data.csv
│   └── insurance_data.csv.dvc
├── dvc_remote_storage/
├── notebooks/
│   └── eda_task1.ipynb
├── src/
│   ├── eda/
│   └── utils/
├── .dvc/
├── .gitignore
├── README.md
└── requirements.txt
```


# 📘 **Task 3 — A/B Hypothesis Testing & Risk Analysis (VDC Project)**

## **📌 Overview**

Task 3 focuses on evaluating whether different customer segments show **significant differences in risk and profitability**.
Using A/B hypothesis testing, we statistically compare provinces, zip codes, and gender groups within the Vehicle Data Challenge (VDC) dataset.

The goal is to determine whether the insurer should differentiate pricing, underwriting rules, or product strategies across these customer groups.

---

## **🎯 Objectives**

This task evaluates four key business hypotheses:

### **H₀₁:** There are *no* risk differences across **provinces**.

### **H₀₂:** There are *no* risk differences across **zip codes**.

### **H₀₃:** There is *no* significant **margin (profit)** difference between zip codes.

### **H₀₄:** There is *no* risk difference between **Men and Women**.

Risk is evaluated using:

* **Claim frequency**
* **Claim severity**
* **Total claims**
* **Margin** (TotalPremium − TotalClaims)

---

## **📊 Methodology**

### **1. KPI Creation**

The following features were engineered:

* **HasClaim** → 1 if TotalClaims > 0
* **Frequency** → % of policies that had ≥1 claim
* **Severity** → Avg. cost per claim
* **Margin** → TotalPremium − TotalClaims

```python
df["HasClaim"] = (df["TotalClaims"] > 0).astype(int)
df["Margin"] = df["TotalPremium"] - df["TotalClaims"]
```

---

### **2. Segmentation (A/B Groups)**

We performed comparisons on:

* **Province A vs Province B**
* **ZipCode1 vs ZipCode2** (largest exposures)
* **Male vs Female customers**
* **High-margin vs low-margin zip codes**

---

### **3. Statistical Tests Used**

| Metric            | Variable Type | Test Used               |
| ----------------- | ------------- | ----------------------- |
| Claim Frequency   | Categorical   | Chi-Square Test         |
| Claim Severity    | Numeric       | t-test / Welch’s t-test |
| Margin            | Numeric       | t-test                  |
| Multi-group tests | Numeric       | One-Way ANOVA           |

Example frequency test:

```python
from scipy.stats import chi2_contingency
tbl = pd.crosstab(df["Province"], df["HasClaim"])
chi2, p, dof, exp = chi2_contingency(tbl)
```

Example margin comparison:

```python
from scipy.stats import ttest_ind
stat, p = ttest_ind(zip1["Margin"], zip2["Margin"], equal_var=False)
```

---

## **📈 Key Findings**

### ✔ **1. Provinces**

* Significant variation in **claim frequency** and **severity** across provinces.
* Some provinces consistently show **higher risk**, suggesting pricing adjustments.

### ✔ **2. Zip Codes**

* Large differences in both **frequency** and **margin**.
* Certain zip codes show **much lower profitability**, rejecting the null hypothesis.

### ✔ **3. Gender**

* No strong statistical evidence that gender impacts risk.
* Supports gender-neutral pricing.

### ✔ **4. Margin Differences**

* Profitability significantly varies between selected zip codes.
* These zip codes may require pricing review or stricter underwriting.

---

## **🧪 Summary of Hypothesis Decisions**

| Hypothesis | Description                              | Result             |
| ---------- | ---------------------------------------- | ------------------ |
| H₀₁        | No risk difference across provinces      | ❌ Rejected         |
| H₀₂        | No risk difference across zip codes      | ❌ Rejected         |
| H₀₃        | No margin difference across zip codes    | ❌ Rejected         |
| H₀₄        | No risk difference between men and women | ✔ Failed to Reject |

---




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







