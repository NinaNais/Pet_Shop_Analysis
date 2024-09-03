# Pet_Shop_Analysis
#### Pet shop analysis using SQL and Power BI



## Table of Contents

- [Project Overview](#overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Exploratory Data Analysis](exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results/Findings](#resultsfindings)
- [Recomendations](#recomendations)
- [Limitations](#limitations)

### Project Overview

In this document, I am exploring the travel agency database to present what information can be obtained using DQL.

This data analysis project aims to provide insights into the sales performance of an e-commerce company over the past year. By analyzing various aspects of the sales data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance.


### Data Sources

The primary dataset for this example is the" file, which contains a detailed travel agency database.

### Tools

Excel - Data Cleaning
SQL Server - Data Analysis
PowerBI - Creating Reports


### Data Cleaning/Preparation

In the initial phase, I performed the following tasks:
-data loading and inspection 
-handling missing values
-data cleaning and formatting


### Exploratory Data Analysis

EDA involved exploring databases to answer questions, such as:

1. What is the current stock status?
2. What is the overall sales trend?
3. Which products are top sellers?
4. What are the peak sales periods?


### Data Analysis

1. What is the current stock status?
```sql
select Sold.Name, Ordered.Ordered_Number-Sold.Sold_Number as Stock_status
from
(select p.Name, sum(s.Amount) as Sold_Number
from Sales s
inner join Products p on s.ProductID=p.ProductID
group by p.Name) Sold
inner join
(select p.Name, sum(obp.Amount) as Ordered_Number
from OrdersByProduct obp
inner join Products p on obp.ProductID=p.ProductID
group by p.Name) Ordered
on Sold.Name=Ordered.Name
order by Stock_status 
```


### Results/Findings

The analysis results are summarized as follows:
1. The company's sales have been steadily increasing over the past year, experiencing a noticeable peak during the holiday season.
2. Product Category A is the best-performing category in terms of sales and revenue.
3. Customer segments with high lifetime value(LIV) should be targeted for marketing efforts. 


### Recomendations

Based on the analysis, I recommend the following actions:
-Invest in marketing and promotion during peak sales seasons to maximize revenue.
-Focus on expanding and promoting products in Category A
- Implement a customer segmentation strategy to target high-LTV customers effectively.


### Limitations

I had to remove all zero values from the budget and revenue columns because would have affected the accuracy of my conclusion from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between both budget and number of votes with revenue.

