
# **Task 1 – Git, GitHub & Exploratory Data Analysis (EDA)**

## **1.1 Git and GitHub**

This task focuses on setting up a proper version-controlled environment for the project and building clean development workflows.

### ✅ **Tasks Completed**

* Created a GitHub repository for the week’s challenge
* Set up Git version control following best practices
* Added a clear and professional README
* Implemented CI/CD using GitHub Actions
* Created a dedicated branch named **`task-1`** for all Day-1 work
* Made multiple commits with descriptive commit messages

### **Key Performance Indicators (KPIs)**

* Proper development environment setup
* Demonstration of Git skills
* Frequent, meaningful commits
* Clean repository organization

---

## **1.2 Project Planning – Exploratory Data Analysis (EDA)**

The goal of EDA is to understand the structure, quality, and patterns within the insurance dataset to guide subsequent statistical testing and modeling.

### ✅ **Data Understanding**

* Reviewed dataset structure
* Identified numerical, categorical, and date-related fields
* Assessed variable meanings (premium, claims, risk indicators, demographics, auto attributes, etc.)

---

## **EDA Tasks Completed**

### **🔹 Data Summarization**

* Computed descriptive statistics for numerical features such as:

  * `TotalPremium`
  * `TotalClaims`
  * `CalculatedPremiumPerTerm`
  * `CustomValueEstimate`
* Inspected distributions, central tendencies, and variability
* Reviewed data types and confirmed proper formatting

### **🔹 Data Quality Assessment**

* Checked for:

  * Missing values
  * Duplicates
  * Incorrect data types
  * Out-of-range values

### **🔹 Univariate Analysis**

* Histograms for numerical variables
* Bar plots for categorical variables
* Distribution checks for:

  * Provinces
  * VehicleType
  * Gender
  * Postal/Zip codes

### **🔹 Bivariate / Multivariate Analysis**

* Explored correlations between:

  * `TotalPremium` vs `TotalClaims`
  * Monthly trends by `TransactionMonth`
  * Risk variations across provinces, gender, vehicle type
* Generated correlation matrix

### **🔹 Geographic & Segment Comparison**

* Compared risk metrics across:

  * Provinces
  * Vehicle makes/models
  * Postal codes

### **🔹 Outlier Detection**

* Box plots for:

  * `TotalClaims`
  * `CustomValueEstimate`
  * `CalculatedPremiumPerTerm`

### **🔹 Visualizations**

Created **3+ clear and insightful visualizations** highlighting:

* Loss Ratio patterns
* Province-wise differences
* Claim severity trends
* VehicleType risk distributions

---

## **Guiding Questions Addressed**

* What is the overall **Loss Ratio** and how does it vary by Province, Gender, and VehicleType?
* Are there outliers affecting claim or premium distributions?
* Are there time-based trends over the 18-month period?
* Which makes/models show highest claim severity?

---
