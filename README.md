# Retail Report

## Table Of Contents
- [Overview](Overview)
- [Data Sources](Data-Sources)
- [Tools Used](Tools-Used)
- [Data cleaning/preparation](Data-cleaning/preparation)
- [Explanatory Data Analysis](Explanatory-Data-Analysis)
- [Data Analysis](Data-Analysis)
- [Result](Result)
- [Limitations](Limitations)
  
## Overview

This report aims at the the sales revenue,quantity, customers and stocks performance in different countries given in th data. It also looked at the trend over time to have insights of the peak period in the calender year, most stocks purchase, top countries by revenue and top customers for rewards.

## Data Sources

Retail Data; The primary dataset used for this report was gotten from kaggle and it contains detailed information about the company.

## Tools Used

- Excel; Data cleaning
- SQL; Data analysis
- Power Bi; Creating reports/visualization

## Data cleaning/preparation

Following Tasks was performed;

1. Data was loaded and inspected
2. Checking of missing values and errors
3. Data cleaning commenced(filtering and sorting)

### Explanatory Data Analysis 

Exploring Data to answer key points

- 1 What is the total revenue generated?
- 2 What is the total number of purchase?
- 3 Which countries are leading by revenue?
- 4 Who are the top customers by revenue?
- 5 When is the peak period in the calender year given?

## Data Analysis
### SQL Codes; 


```
--DATA LOOK THROUGH
SELECT 
  * 
FROM 
  online_retail; 

--Total Revenue
SELECT 
  SUM(quantity * unitprice) AS Total_revenue 
FROM 
  online_retail; 

--Total Purchase
SELECT
  COUNT(
    DISTINCT(InvoiceNo)
  ) AS Total_purchase 
FROM 
  online_retail; 

  --Average Unit Price
  SELECT
	ROUND(
		AVG(unitprice),
		2
		)AS AverageUnitPrice
FROM
	online_retail;

--Total Number of customers
SELECT 
  COUNT(
    DISTINCT(CustomerID)
  ) AS Total_purchase 
from 
  online_retail; 

-- TOP 10 Countries by revenue
SELECT
  Country,
  ROUND(
    SUM(quantity * unitprice), 
    2
  ) AS Total_revenue 
FROM 
  online_retail 
GROUP BY 
  Country 
ORDER BY 
  Total_revenue DESC; 

--Top 10 Customers For Rewards
SELECT 
  TOP 10 CustomerID, 
  ROUND(
    SUM(quantity * unitprice), 
    2
  ) AS Total_revenue 
FROM 
  online_retail 
GROUP BY 
  CustomerID 
ORDER BY 
  Total_revenue DESC;

--Peak Month by revenue
SELECT
  YEAR(
		invoicedate
	) AS YEAR,
  MONTH(
		invoicedate
	) AS Month,
  ROUND(
    SUM(quantity * unitprice), 
    2
   ) AS Total_revenue  
FROM 
  online_retail 
GROUP BY 
  MONTH(invoicedate)
ORDER BY 
  Total_revenue DESC
``` 


## Result
### The analysis result is summarized below;
- There was increase in revenue towards winter which peaked in october,2011
- The top countries by revenue was analyzed which seems to have a great potential for growth
  with the Netherlands leading the chart by revenue 
- Top 10 customers by revenue was listed out for rewards
- The company's stock performance was carefully analyzed to know the top performing stocks

### Limitations
There were errors in some of the value input which was cleaned using excel,
Further analysis could have been done if the data had more information. 
