# Credit-Card-Report-Analysis-
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

---

## 🛠️ Tools & Technologies Used
- **Microsoft SQL Server** – Data storage, cleaning, and querying
- **Power BI** – Data visualization and dashboard creation
- **DAX (Data Analysis Expressions)** – Custom calculations and measures
- **CSV** – Source data format

---

---

## 🔄 Data Processing Strategy

- Data was first imported from **CSV into SQL Server**.
- **Data cleaning** was done at the SQL level for better performance in Power BI.
  - Removed null values and duplicates.
  - Bucketed values like age and income into logical groups for better visuals.
- Data was then imported into Power BI from SQL Server.

### 🧹 Data Transformation in SQL
- Pre-cleaning before Power BI import
- Ensured consistent datatypes, handled missing data

---

## 🧠 DAX Calculations

### ➤ Age Group Column:
```DAX
AgeGroup = SWITCH(
    TRUE(), 
    cust_detail[Customer_Age] < 30, "20-30",
    cust_detail[Customer_Age] >= 30 && cust_detail[Customer_Age] < 40 , "30-40",
    cust_detail[Customer_Age] >= 40 && cust_detail[Customer_Age] < 50 , "40-50",
    cust_detail[Customer_Age] >= 50 && cust_detail[Customer_Age] < 60 , "50-60",
    cust_detail[Customer_Age] >= 60, "60+",
    "unknown"
)
