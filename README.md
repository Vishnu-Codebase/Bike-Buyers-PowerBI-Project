# 🚲 Bike Buyers Analysis – Power BI Project

## 📌 Project Overview

This Power BI project analyzes a **Bike Buyers dataset** to understand customer demographics and purchasing behavior.
The goal of the analysis is to identify **factors influencing bike purchases** such as age, income, commute distance, region, and occupation.

The project demonstrates **end-to-end Business Intelligence workflow**, including:

* Data Cleaning
* Data Transformation
* Feature Engineering
* Data Modeling
* DAX Measures
* Interactive Report Design
* Drilldown & Drillthrough
* Bookmarks and Navigation

The final Power BI report provides **interactive insights into customer behavior and purchasing trends**.

---

# 📂 Dataset Information

Dataset: **Bike Sales Dataset**

The dataset contains customer demographic information and purchase behavior.

### Main Columns

* Customer_ID
* Age
* Income
* Gender
* Marital_Status
* Children
* Education
* Occupation
* Home_Owner
* Cars
* Commute_Distance
* Region
* Purchased_Bike

Each record represents **one customer and their bike purchasing status**.

---

# 🧹 Data Cleaning & Transformation (Power Query)

Data preparation was performed using **Power Query Editor**.

### Steps Performed

1. Promoted column headers.
2. Removed unnecessary columns.
3. Standardized categorical values.
4. Replaced coded values with meaningful labels.

Example transformations:

| Original Value | Replaced With |
| -------------- | ------------- |
| M              | Married       |
| S              | Single        |

### Commute Distance Cleaning

Original values:

```
0-1 Miles
1-2 Miles
2-5 Miles
5-10 Miles
10+ Miles
```

Cleaned values:

```
0-1
1-2
2-5
5-10
10+
```

---

# 🧠 Feature Engineering

New features were created to improve analytical insights.

### Age Group

Customers were categorized into age segments:

| Age   | Age_Group |
| ----- | --------- |
| <30   | Young     |
| 30–45 | Adult     |
| 45+   | Senior    |
| <70   | Elder     |
---

### Income Group

Income values were grouped into categories:

| Income | Income_Group  |
| ------ | ------------- |
| Low    | Low Income    |
| Medium | Medium Income |
| High   | High Income   |

---

### Commute Category

Commute distances were categorized for analysis.

| Commute Distance | Commute_Category |
| ---------------- | ---------------- |
| 0-1              | Very Short       |
| 1-2              | Short            |
| 2-5              | Medium           |
| 5-10             | Long             |
| 10+              | Very Long        |

---

# 🗂 Data Modeling

Although the dataset originated from **a single Excel table**, it was split into two logical tables to demonstrate **data modeling principles**.

### Fact Table

`Fact_BikeSales`

Contains transactional or measurable data.

Columns:

* Customer_ID
* Age
* Income
* Cars
* Children
* Commute_Distance
* Purchased_Bike

---

### Dimension Table

`Dim_Customer`

Contains descriptive customer attributes.

Columns:

* Customer_ID
* Gender
* Marital_Status
* Education
* Occupation
* Home_Owner
* Region
* Age_Group
* Income_Group
* Commute_Category

---

### Relationship

```
Dim_Customer[Customer_ID]
        │
        │ 1 : 1
        │
Fact_BikeSales[Customer_ID]
```

This structure demonstrates **star schema principles and relational modeling**.

---

# 📐 DAX Measures

Several measures were created using **DAX (Data Analysis Expressions)**.

### Total Customers

```DAX
Total Customers =
COUNT(Fact_BikeSales[Customer_ID])
```

---

### Bike Buyers

```DAX
Bike Buyers =
CALCULATE(
COUNT(Fact_BikeSales[Customer_ID]),
Fact_BikeSales[Purchased_Bike] = "Yes"
)
```

---

### Non Bike Buyers

```DAX
Non Bike Buyers =
CALCULATE(
COUNT(Fact_BikeSales[Customer_ID]),
Fact_BikeSales[Purchased_Bike] = "No"
)
```

---

### Average Age

```DAX
Avg Age =
AVERAGE(Fact_BikeSales[Age])
```

---

### Average Income

```DAX
Avg Income =
AVERAGE(Fact_BikeSales[Income])
```

---

### Bike Purchase Rate

```DAX
Bike Purchase Rate =
DIVIDE([Bike Buyers], [Total Customers],0)
```

---

# 📊 Report Pages

The Power BI report contains **multiple analytical pages**.

---

## 1️⃣ Customer Overview

Provides a high-level summary of all customers.

Visuals included:

* KPI Cards

  * Total Customers
  * Bike Buyers
  * Non Bike Buyers
  * Average Age
  * Average Income
* Customers by Region
* Customers by Occupation
* Purchase Distribution (Yes vs No)
* Matrix: Region → Occupation vs Purchase
* Customer detail table

---

## 2️⃣ Bike Buyers Customer Overview

Focuses on customers who purchased bikes.

Visuals included:

* Bike Buyers by Age Group
* Bike Buyers by Region
* Bike Buyers by Income Group
* Bike Buyers by Commute Category
* Bike Buyers vs Car Owners
* Purchase Distribution

---

## 3️⃣ Demographic Analysis

Analyzes demographic characteristics of customers.

Visuals included:

* Matrix: Gender → Children vs Purchased Bike
* Customers by Children vs Purchase
* Non Bike Customers by Commute Category
* Bike Customers by Commute Category
* Demographic comparison charts

---

## 4️⃣ Purchase Behavior

Examines factors influencing bike purchases.

Visuals included:

* Bike Buyers by Income Group
* Bike Buyers by Commute Distance
* Bike Buyers vs Cars Owned
* Bike Buyers by Region
* Purchase Rate by Region
* Matrix: Income Group vs Commute Category

---

## 5️⃣ Customer Details (Drillthrough Page)

Provides detailed customer-level analysis.

Features:

* Drillthrough from charts
* Customer data table
* Back navigation button

Columns displayed:

* Customer_ID
* Age
* Gender
* Income
* Occupation
* Cars
* Children
* Region
* Commute_Category
* Purchased_Bike

---

# 🎛 Interactive Features

The report includes multiple interactive BI features.

### Slicers

* Region
* Gender
* Occupation
* Income Group
* Commute Category

### Drill Down

Matrix visuals support hierarchical exploration.

### Drillthrough

Users can navigate from summary visuals to detailed customer data.

### Bookmarks

Used for **Reset Filters functionality**.

### Navigation Buttons

Buttons allow quick navigation across report pages.

---

# 🎨 Report Design

Report design follows modern Power BI layout practices.

Canvas Size:

```
1280 × 720
```

Design elements:

* Clean layout
* Consistent color theme
* Interactive visuals
* Dropdown slicers
* Responsive filtering

---

# 🔍 Key Insights

Key findings from the analysis include:

* Middle age customers show higher bike purchase rates.
* Customers with shorter commute distances are more likely to buy bikes.
* Higher income groups show stronger purchase behavior.
* Occupation and region influence bike purchase decisions.

---

# 🛠 Tools Used

* Microsoft Power BI Desktop
* Power Query
* DAX (Data Analysis Expressions)
* Data Modeling
* Interactive Visualizations

---

# 📁 Repository Structure

```
Bike-Buyers-PowerBI-Project

│
├── Bike_Buyers_Report.pbix
├── Bike_Sales_Data.xlsx
├── README.md
└── screenshots
    ├── customer_overview.png
    ├── bike_buyers_overview.png
    ├── demographic_analysis.png
    └── purchase_behavior.png
```

---

# 🚀 Project Purpose

This project demonstrates practical skills required for **Business Intelligence and Data Analyst roles**, including:

* Data transformation
* Data modeling
* DAX calculations
* Data visualization
* Interactive report design

---

# 📬 Author

**Vishnuraj M**

Aspiring Data Analyst focused on **Power BI, Data Analytics, and Business Intelligence**.

---
