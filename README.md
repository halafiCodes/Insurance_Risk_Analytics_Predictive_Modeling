

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




