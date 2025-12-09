

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


