

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






