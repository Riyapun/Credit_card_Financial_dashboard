# 💳 Credit Card Financial Dashboard

This project is a dynamic, interactive financial dashboard created using **Power BI**, **SQL**, and **Excel**. It aims to visualize customer credit card transactions and behavior for financial analysis and business insights.

Developed as part of a portfolio and academic submission, the dashboard demonstrates skills in data processing, dashboard design, and analytics storytelling.

---

## 🎯 Objective

To design a credit card usage dashboard that allows users to:

- Track monthly credit card spending
- Understand category-wise expenses
- Analyze customer payment patterns and outstanding balances
- Visualize trends and KPIs in an intuitive format

---

## 🛠 Tools & Technologies Used

- **Power BI Desktop** – for data modeling and dashboard visualization  
- **Microsoft Excel** – for raw data cleaning and transformation  
- **SQL** – for data preprocessing and joins  
- **DAX (Data Analysis Expressions)** – for creating custom measures and KPIs  

---

## 📂 Dataset

> **Note**: The data used in this project is completely synthetic/mock data, created for learning and presentation purposes.

### Data Files:
- `public_cc_details.csv` – credit card transactions  
- `public_cust_details.csv` – customer demographics and basic info  

These datasets were joined and processed using SQL, then loaded into Power BI for visualization.

---

## 📊 Dashboard Features

- 📈 Total Spend by Customer  
- 📆 Monthly Spending Trends  
- 🧾 Category-wise Expense Breakdown  
- 💰 Outstanding Balance Tracker  
- 👥 Filterable by Month, Customer ID, and Transaction Category  
- 📍 KPI Cards for Spend, Payment, and Customer Count  

---

## 🧠 DAX Measures Used

```dax
-- Total Credit Card Spend
Total Spend = SUM(public_cc_details[Amount])

-- Monthly Spend Trend
Monthly Spend = 
CALCULATE(
    [Total Spend],
    FILTER(
        ALL(public_cc_details[Transaction_Date]),
        public_cc_details[Transaction_Date]
    )
)

-- Outstanding Balance
Outstanding Balance = 
SUM(public_cc_details[Amount]) - SUM(public_cc_details[Payments])

-- Unique Customers
Customer Count = DISTINCTCOUNT(public_cust_details[Customer_ID])

💾 SQL Queries Used (Preprocessing)
sql
Copy
Edit
-- Join customer and transaction data
SELECT 
    c.Customer_ID,
    c.Name,
    cc.Transaction_ID,
    cc.Amount,
    cc.Transaction_Date,
    cc.Category
FROM public_cust_details c
JOIN public_cc_details cc
    ON c.Customer_ID = cc.Customer_ID;

-- Monthly Spend Aggregation
SELECT 
    Customer_ID,
    FORMAT(Transaction_Date, 'yyyy-MM') AS Month,
    SUM(Amount) AS Total_Spend
FROM public_cc_details
GROUP BY Customer_ID, FORMAT(Transaction_Date, 'yyyy-MM');

Access Dashboard File
If the .pbix file exceeds GitHub’s 100MB limit, you can download it here:

  🔗 Download CreditCardDashboard.pbix


##👩‍💻 Author

 Reshma Pun
 📚 Final Year BCA (Data Science)
 📫 GitHub Profile

##📜 License
This project is licensed under the MIT License

