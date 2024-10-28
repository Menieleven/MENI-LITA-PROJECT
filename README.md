# LITA-PROJECT

## TABLE OF CONTENT
### [PROJECT OVERVIEW] (Preview overview) 
### DATA SOURCES
### DATA FORMS
### TOOLS USED
### DATA CLEANING AND PREPARATION
### EXPLORATORY DATA ANALYSIS
### DATA VISUALISATION
### This project gives the detailed documentation of LITA DATA ANALYSIS Project work

PROJECT TITLE: LITA CAPSTONE DATA ANALYSIS FOR SALES PERFORMANCE ANALYSIS
PROJECT OVERVIEW
In this project, you are tasked with analyzing the sales performance of a retail store. 
AIMS AND OBJECTIVE: explore sales data to uncover key insights such as top-selling products, regional 
performance, and monthly sales trends and produce an interactive Power BI
dashboard highlighting these findings.


## INTRODUCTION

DATA SOURCE
excel file
csv file
TOOLS USED
Microsoft Excel Download Here
for Data Cleaning
Analysis and
visualization
SQL - Structured Query Language
Quering of Data
Power BI - Power Business Intelligent
Data visualisation
Report
EXPLORATORY DATA ANALYSIS DATA ANALYSIS
This is where I include some line of code, queries or some of the DAX expressions used during th analysis; ###WITH EXCEL In the initial phase of data cleaning and preparations, I perform the following actions;

Data loading and inspection
Handling missing variables
Data Cleaning and Formatting
visualization of key findings
To use pivot:
Highlight or click on any cell within your data range
Go to the insert Tab
Click on the pivot  table button to open a dialog box
Select Data Range
Choose where to place the pivot table (a new worksheet or in the existing worksheet)
Build customize and format the table
Summarize total sales by Product
TOTAL SALES OR REVENUE BY PRODUCT
Summarize total sales by Region
TOTAL SALES BY REGION
Summarize total sales by Month
SUM OF TOTAL REVENUE BY MONTH
Average Sales per product CAPSTONE AVERAGE SALES PER PRODUCT

Sum of total revenue by Region
SUM OF TOTAL REVENUE BY REGION

Sum of total Revenue by Region using excel function SUMIF

=SUMIF(range,criteria,[sum_range])
WHERE;

Range : the range of cells to evaluate, in this sense region
Criteria: the condition that must be met (can be any of the 4 regions in this analysis- )
Sum_range: the actual cell to sum
=SUMIF(D2:D50001,D2,H2:H50001)
TOTAL REVENUE BY REGION USING EXCEL FUNCTION SUMIF 
8.Average sales per product

=AVERAGEIF(range,criteria,[average_range])
WHERE;

Range : the range of cells to evaluate, in this sense product
Criteria: the condition that must be met (can be any of the 6 products in this analysis)
Average_range:the actual cell to average
=AVERAGEIF(C2:C50001,C49988,H2:H50001)
AVERAGE SALES BY PRODUCT USING EXCEL FUNCTION AVERAGE IF
Percentage Revenue by Region
PERCENTAGE REVENUE BY REGION
Percentage sales by product
SALES PER PRODUCT IN PERCENTAGE
EXPLORATORY DATA ANALYSIS (WITH SQL)
Convert excel sheet to csv
Remove headers
import the csv to my sql
Ensure to format the the date column into YYY-MM-DD while importing the csv into my sql
Top selling product by total sales value
SELECT Product, SUM(TotalSales) As TotalSales
FROM orders
GROUP BY TotalSales DESC
LIMIT 1;
Total sales for each product category
SELECT Product, SUM(Totalsales) As TotalSales
FROM orders
GROUP BY Product;
Number of sales transaction in each region
SELECT Region, COUNT(*)As NumberOfTransaction
FROM Orders
GROUP BY Region;
4.Total revenue per product

SELECT Product, SUM(TotalSales)As TotalRevenue
FROM Orders
GROUP BY Product;
5.Monthly sales total for the current year

SELECT MONTH(OrderDate)As Month, SUM (TotalSales)As MonthlySales
FROM Orders
WHERE YEAR(OrderDate)=YEAR(CURDATED())
GROUP BY MONTH(OrderDate)
ORDER BY MONTH;
Top 5 customer by totalpurchase amount
SELECT CustomerID,SUM(TotalSales) As TotalPurchase
FROM orders
GROUP BY CustomerID
ORDER BY TotalPurchase DESC
LIMIT 5;
Percentage of total sales contributed by each region
SELECT Region,
SUM(TotalSales) As TotalSales,
(SUN(TotalSaless)/(SELECTSUM(TotalSales)FROM orders)*100) As PercentageOfTotalSales
FROM orders
GROUP BY Region;
Products with no sale in the last quarter
SELECT DISTINCT Product
FROM orders
WHERE Product NOT IN(
SELECT Product
FROM orders
WHERE OrderDate>=DATE_SUB(CURDATE(),INTERVAL 3 MONTH)
);
EDA involves the exploring of Data to answer some questions about the Data such as;

top-selling product
monthly sales trend
sales for each product category
number of sales transaction in each region
highest selling product by total sales value
total revenue per product
monthly sales total for the current year
the top 5 customers by total purchase amount
percentage of total sales contributed by Each region
identify product with no sales in the last quarter
