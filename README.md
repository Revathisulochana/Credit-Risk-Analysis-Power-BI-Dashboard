# 📊 Credit Risk Analysis Dashboard | Power BI Project

An end-to-end **Credit Risk Analysis Dashboard** built using **Microsoft Excel, Power BI, Power Query, and DAX**. This project demonstrates the complete data analytics workflow—from data cleaning and transformation to data modeling, DAX calculations, and interactive dashboard creation for credit risk analysis.

---

## 📌 Project Overview

The objective of this project is to analyze customer credit risk by transforming raw loan data into meaningful business insights. The dashboard helps financial institutions monitor loan portfolios, identify high-risk customers, and support data-driven lending decisions.

---

## 🛠️ Tools & Technologies

- Microsoft Excel
- Power BI Desktop
- Power Query
- DAX (Data Analysis Expressions)

---

## 📂 Dataset

### File 1 – Credit Risk Analysis

Contains customer loan information such as:

| Loan ID |
| Credit Amount |
| Credit History |
| Employment |
| Savings Status |
| Age |
| Housing |
| Loan Duration |
| Existing Credits |
| Property |
| Loan Purpose |
| Gender |
| Foreign Worker |

### File 2 – City List

Used for geographical analysis.

| Loan ID |
| State |
| City |

---

# 📋 Data Cleaning (Excel)

### ✔ Header Standardization

- Identified inconsistent text formats in column headers.
- Standardized headers using **Find & Replace**.

---

### ✔ Data Alignment

Applied Excel's **PROPER()** function to standardize text capitalization.

```excel
=PROPER(A2)
```

---

### ✔ Employment Category Standardization

Used **Find & Replace** to improve readability.

| Original Value | Updated Value |
|---------------|---------------|
| >=7 | 7 Years |
| 1<=X<4 | 1–4 Years |
| 4<=X<7 | 4–6 Years |
| <1 | Below 1 Year |

---

# 🔄 Power Query Transformations

- Imported both datasets.
- Changed **Credit_Amount** data type to **Currency**.
- Verified column data types.
- Loaded transformed data into the Power BI data model.

---

# 🧮 DAX Calculated Columns

## Risk Level

```DAX
Risk Level =
SWITCH(
    TRUE(),
    'Credit Risk Analysis-1'[Credit_History]="Critical/Other Existing Credit","High Risk",
    'Credit Risk Analysis-1'[Credit_History]="Delayed Previously","Medium Risk",
    'Credit Risk Analysis-1'[Credit_History]="Existing Paid","Low Risk",
    "Very Low Risk"
)
```

---

## Age Group

```DAX
Age Group =
SWITCH(
    TRUE(),
    'Credit Risk Analysis-1'[Age]<=20,"Teen",
    'Credit Risk Analysis-1'[Age]<=30,"Young Adult",
    'Credit Risk Analysis-1'[Age]<=45,"Adult",
    "Senior"
)
```

---

# 📊 DAX Measures

### Average Age

```DAX
Average Age =
AVERAGE('Credit Risk Analysis-1'[Age])
```

### Average Credit Amount

```DAX
Average Credit Amount =
AVERAGE('Credit Risk Analysis-1'[Credit_Amount])
```

### Average Duration

```DAX
Average Duration =
AVERAGE('Credit Risk Analysis-1'[Duration])
```

### High-Risk Customers

```DAX
High-Risk Customer =
CALCULATE(
    [Total Loan],
    'Credit Risk Analysis-1'[Risk Level]="High Risk"
)
```

### Low-Risk Customers

```DAX
Low-Risk Customers =
CALCULATE(
    [Total Loan],
    'Credit Risk Analysis-1'[Risk Level]
        IN {"Low Risk","Very Low Risk"}
)
```

### Total Loans

```DAX
Total Loan =
COUNTROWS('City List')
```

### Total Loan Amount

```DAX
Total Loan Amount =
SUM('Credit Risk Analysis-1'[Credit_Amount])
```

---

# 🔗 Data Modeling

Relationship created using **Loan ID**.

| Table | Relationship | Table |
|--------|--------------|-------|
| Credit Risk Analysis | Loan ID | City List |

- One-to-Many Relationship
- Single Cross Filter Direction
- Optimized for better report performance

---

# 📈 Dashboard Features

### KPI Cards

- 💰 Total Loan Amount
- 📄 Total Loans
- ⚠️ High-Risk Customers
- ✅ Low-Risk Customers
- 👤 Average Age

### Interactive Visuals

- Employment vs Risk Level
- Risk Level Distribution
- Loan Amount vs Age by Risk Level
- High-Risk Customers by City (Map)
- Savings Status Distribution
- Risk Level vs Credit History (Matrix)

### Interactive Filters

- City
- State
- Loan Purpose
- Gender

### Additional Features

- Clear All Slicers Button
- Interactive Cross Filtering
- Dynamic KPI Cards

---

# 📊 Key Business Insights

- 18% of customers are High Risk, contributing ₹12.4 Cr of the total loan portfolio.
- 64% of high-risk customers have No Savings or Savings below ₹10,000.
- 57% of risky loans belong to customers with Critical or Delayed Credit History.
- Customers with loan amounts above ₹8 Lakhs show a 2.1× higher default risk.
- 41% of high-risk customers are Unemployed or have less than 1 year of employment.
- Business and Used Car loans contribute 46% of the total high-risk portfolio.
- Customers with two or more existing loans are 1.8× more likely to default.
- 72% of low-risk customers own property (House/Real Estate).
- Customers with 7+ years of employment have a 28% lower default rate than new employees.
- Improving approval accuracy by just 5% could reduce expected loan losses by approximately ₹1.8 Cr annually.

---
# 📊 Key Business Improvement
- Tighten credit approval rules and require additional verification for high-risk applicants.
- Introduce stricter eligibility criteria and request additional collateral for low-savings customers.
- Increase the weight of credit history in the credit scoring model before loan approval.
- Set loan amount limits or charge risk-based interest rates for large loans.
- Verify income stability and require guarantors for applicants with unstable employment.
- Review lending policies and reduce exposure in high-risk loan categories.
- Limit new loan approvals for customers with high existing debt obligations.
- Offer pre-approved loans and premium products to property-owning customers.
- Reward long-term employed customers with faster approvals and better interest rates.
- Implement predictive analytics and AI-based credit risk models for better lending decisions.

---
# 🎯 Skills Demonstrated

- Data Cleaning
- Data Transformation
- Excel Functions
- Power Query
- DAX
- Data Modeling
- Power BI Visualization
- Dashboard Design
- KPI Development
- Credit Risk Analysis
- Financial Analytics
- Business Intelligence

---

# 🚀 Learning Outcomes

This project helped strengthen practical knowledge of:

- Excel Data Cleaning
- Power Query Transformations
- DAX Calculations
- Data Modeling
- Interactive Dashboard Development
- Financial Data Analysis
- Credit Risk Analytics
- Business Intelligence Reporting

---

# 📷 Dashboard Preview
<img width="574" height="325" alt="image" src="https://github.com/user-attachments/assets/61f2940d-ccae-483f-aae8-1bcbd76c80a3" />


---

# 📁Repository Structure

```
Credit-Risk-Analysis-Dashboard
│
├── 📁 Dataset
│   ├── Credit Risk Analysis.xlsx
│   └── City List.xlsx
│
├── 📁 Dashboard
│   └── Credit Risk Analysis Dashboard.pbix
│
├── 📁 Images
│   └── Dashboard Preview.png
│
├── 📄 README.md
├── 📄 LICENSE
└── 📄 .gitignore
```
