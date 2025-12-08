# Bank and Customer Churn Analysis

## Project Overview
This repository contains documents and resources relating to a bank and customer churn analysis of a fictitious bank.

The project was carried out using **Power Query** for data transformation and **Power BI** for visualizing insights.  
It also involved the use of **DAX** for calculations and logical measures.

### Tools Used
- Power Query — data transformation  
- Power BI — dashboard creation and visualization  
- DAX — calculated measures and analytics  

---

## Project Goal
The primary goal of this project is to practically apply **Power Query**, **Power BI**, and **DAX** to transform, model, and visualize data.

The final **Power BI interactive dashboard** answers the following questions:

1. Which country has the highest customer churn rate?  
2. What is the churn rate by gender?  
3. How does credit score range affect churn rate?  
4. Do customers with credit cards churn more or less?  
5. Are active members less likely to churn?  
6. What is the average balance of churned vs retained customers?  
7. How does age relate to customer churn?  
8. Is there a relationship between tenure and churn rate?  
9. How does the number of products held affect churn?  
10. Does estimated salary influence the likelihood of churn?  
11. What is the churn distribution across different age groups (18–25, 26–35, etc.)?  
12. Which combination of factors (e.g., geography + gender) shows the highest churn?  
13. Do customers with zero balance churn more than those with money in their account?  
14. Is there a link between high credit score and being an active member?  
15. What is the churn rate among customers with long tenure (5+ years) compared to new ones?  

---

## Features
- Interactive **Power BI dashboard** with slicers (Age Group, Country, Gender)  
- Includes a file containing all **DAX formulas** used in the report  

---

## Data

### Raw Dataset
The original dataset used for this analysis can be found in the folder below:

- **Bank and Customer Churn Dataset Folder:**  
  [Download Here](https://github.com/ifioklee/Bank-and-Customer-Churn-Analysis/tree/main/Bank%2BCustomer%2BChurn)

### DAX Scripts
This file contains all the DAX formulas used in this analysis:  
[View DAX Formula Script](#)

### Visualization
Interactive Power BI dashboard:  
[View Power BI Dashboard](https://github.com/ifioklee/Bank-and-Customer-Churn-Analysis/blob/main/Bank%20Churn%20Analysis.pbix)

### README Documentation
Full project documentation:  
[View README File](https://github.com/ifioklee/Bank-and-Customer-Churn-Analysis/blob/main/README.md)

---

## Technical Details

### Data Preparation & Transformation (Power Query)

### 1. Account Information Table
- Changed **CustomerId** data type to text  
- Removed two columns with all NULL values  
- Created a **Balance** column with numeric values only by removing the Euro (€) symbol using *Split Column by Example*

### 2. Customer Information Table
- Removed six columns containing only NULL values  
- Changed **CustomerID** data type to text  
- Created a new **EstimatedSalary** column without the Euro (€) symbol and set it to fixed decimal  
- Replaced "FRA" and "French" with "France" in the **Geography** column  
- Renamed **Geography** column to **Country**

The **Account Information Table** and **Customer Information Table** were merged and rearranged to match the structure of the **Bank Customer Table**.

### 3. Bank Customer Table
- Changed **CustomerId** data type to text  
- Appended merged Account & Customer tables to the main Bank Customer table  
- Created **Age Group** using conditional logic:
  - Youth (< 26)  
  - Young Adult (< 36)  
  - Middle Age (< 46)  
  - Senior Adult (< 61)  
  - Elderly (≤ 92)  

- Created **Credit Score Range**:
  - 350–395 → Very Low  
  - ≤ 435 → Low  
  - ≤ 475 → Medium  
  - Else → High  

- Created **Tenure Range**:
  - 1–2 Years  
  - 3–4 Years  
  - 5–6 Years  
  - 7–8 Years  
  - 9–10 Years  

- Created **Salary Range**:
  - ≤ 40,000 → Low  
  - ≤ 80,000 → Lower-Middle  
  - ≤ 120,000 → Middle  
  - ≤ 160,000 → Upper-Middle  
  - Else → High  

- Created **Tenure Group**:
  - ≥ 5  → Long Tenure (5+ yrs)  
  - < 1  → New Customer  
  - Else → Other  

All transformations were then loaded into **Power BI**.

---

## Visualizations in Power BI
- **Six Card Visuals**:
  - Number of Customers  
  - Churned Customers  
  - Number of Products  
  - Number of Countries  
  - Average Balance (Churned)  
  - Average Balance (Retained)  

- **Donut Chart** → Churn Rate by Country  
- **Stacked Bar Charts** → Churn by Age Group & Credit Score Range  
- **Pie Chart** → Churn by Gender  
- **Table Visuals**:
  - Churn by Tenure  
  - Product Count vs Churn  
  - Balance Category Churn  
  - Tenure Group Churn  

- **Matrix Table**:
  - Active Member Churn  
  - Credit Card Ownership Churn  
  - Geo-Gender Churn Breakdown  

- **Clustered Column Chart** → Salary Range Churn  
- **Three Slicers** → Age Group, Country, Gender  
- **Two Navigation Buttons** → Dashboard page switching  

---

## Results & Insights

- **Total Customers Analyzed:** 10,000  
- **Countries:** 3  
- **Product Lines:** 4  
- **Total Churned Customers:** 2,037  
- **Overall Churn Rate:** 20.37%  

### Key Findings

1. **Germany** had the highest churn with **814 customers (39.96%)**, followed closely by France. Spain had the lowest churn.
2. **Females churned more than males**, accounting for **55.92%** of churned customers.
3. **Credit Score Impact:**
   - Very Low → 100% churn  
   - Low → 27%  
   - Medium → 19.67%  
   - High → 20.17%  
4. **Customers with credit cards churn less** than those without.
5. **Active members are less likely to churn** than inactive members.
6. **Average Balance:**
   - Churned → €91,109  
   - Retained → €72,745  
7. **Churn rate increases with age.**
8. **Tenure Churn Rates:**
   - 1–2 years → 21.15%  
   - 3–4 years → 20.82%  
   - 5–6 years → 20.46%  
   - 7–8 years → 18.22%  
   - 9–10 years → 21.30%  
9. Customers holding **4 products churned the most (100%)**, while those with **2 products churned the least (7.58%)**.
10. **Estimated salary has no significant effect** on churn likelihood.
11. Across all countries, **female customers churn more than male customers**.
12. **Customers with zero balance churn more** than those with positive balances.
13. **Long-tenure customers (5+ years) churn at 19.85%**, while **new customers churn at 23%**.

