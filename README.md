# LITA-PROJECT

### Project Title: Sales Performance Analysis

### Project Overview
---
This project involves analyzing the sales performance of a retail store to identify essential insights, including top-selling products, regional sales performance and monthly sales trends. the objective is to explore and interpret the sales data, providing a comprehensive view of the store's performance. These findings will be presented through Microsoft Excel, Structured Query Language (SQL) and an interactive Power BI dashboard, which would enable data-driven decisions. 

### Data Source
---
The dataset used in this project is the LITA Capstone Dataset (Sales Data). This Data was provided by our instructors specifically for analysis purposes, which helped to stimulate real-world scenarios for analysis.

### Tools Used
---
- Mircosoft Excel for Data Cleaning, Analysis and Visualization
- Structured Query Language (SQL) for Querying of Data
- Power Bi for Advanced Visualizations and Interactive Reports
- GitHub for Portfolio Building

 ### Data Cleaning and Prepartions

  ### Exploratory Data Analysis
  ---
  Below are some of the question answerwed while exploring the Dataset;
- Microsoft Excel
    1. Using pivot tables summarize Total sales by product, region and month.
    2. Use Excel formulas to calculate the metrics such as average sales per product and total revenue by region.
    3. Create any other interresting reports.

- Structured Query Language (SQL)
   1. Retrieve the total sales for each product category.
   2. Find the number of sales transactions in each region.
   3. Find the highest selling product by total sales value.
   4. Calculate total revenue per product.
   5. Calculate monthly sales totals for the current year.
   6. Find the top 5 customers by total purchase amount.
   7. Calculate the percentage of total sales contributed by each region.
   8. Identify products with no sales in the last quarter.

- Power BI
  1. Create a dashborad that visualizes the insights found in Excel and SQL. The dashboard should include a sales overview, top-performing products and regional breakdowns.
 
  ### Data Analysis
  ---
  - Mircosoft Excel
 Below are some analysis done on the data:
1. Total sales by product, region, month using pivot tables
   
3. Average sales per product and total revenue by region using excel formulas such as AVERAGEIF and SUMIF
   
  - SQL

 Below are some queries used during analysis: 
```SQL
SELECT * FROM [dbo].[SalesData]

---Total sales for each product category 
select Product , SUM(Total_Sales) as Total_Sales_per_Product
from [dbo].[SalesData]
group by Product

---Number of sales transaction in each region
select Region, COUNT (Total_Sales) as No_of_Sales_Transactions
from [dbo].[SalesData]
group by region

---Highest selling product by total sales value
select top 1 Product , sum(Total_Sales) as Total_Sales
from [dbo].[SalesData]
group by Product
order by SUM(Total_Sales) desc

---Total Revenue per Product
select Product , SUM(Total_Sales) as Total_Revenue_per_Product
from [dbo].[SalesData]
group by Product

---Monthly Total Sales for the current Year
select MONTH (OrderDate) as MONTH,
sum (Total_Sales) as Monthly_Sales_Total
from [dbo].[SalesData]
where year(OrderDate) =2024
group by month(OrderDate)
order by month (OrderDate);

---Top 5 customer by Total Sales
select top 5 Customer_Id , 
SUM(Total_Sales) as Total_Purchase_Amount
from [dbo].[SalesData]
group by Customer_Id
order by SUM(Total_Sales)desc

---Percentage of total sales contributed by each region
with totalSales as (select SUM(Total_Sales) as TotalSalesAmount from [dbo].[SalesData])
select Region, SUM(Total_Sales) as Region_Total_Sales,
(SUM(Total_Sales) * 100/ (select TotalSalesAmount from totalSales)) as Percentage_of_Total_Sales
from [dbo].[SalesData]
group by Region

--- Prodcts with no sales in the last quarter
select Product from [dbo].[SalesData]
group by Product
Having sum (CASE WHEN OrderDate between '2024-06-01' AND '2024-08-31'
THEN 1 ELSE 0 End) = 0
```

### Data Visualization

  

  
   
