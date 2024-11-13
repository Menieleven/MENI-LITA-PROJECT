# LITA-PROJECT 1
This project gives the detailed documentation of LITA DATA ANALYSIS Project work

### PROJECT TITLE: LITA CAPSTONE DATA ANALYSIS FOR SALES PERFORMANCE ANALYSIS
## PROJECT OVERVIEW:
In this project, you are tasked with analyzing the sales performance of a retail store. 

AIMS AND OBJECTIVE: explore sales data to uncover key insights such as top-selling products, regional 
performance, and monthly sales trends and produce an interactive Power BI
dashboard highlighting these findings.

### DATA SOURCES
The main data source is the Capstone data uploaded to the learners' database. 
this is an open source data downloaded from my dashboard on the LMS learning platform

### TOOLS USED
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1.  For Data Cleaning
  2.  For Analysis
  3.  For Data Visualization
     
- Microsoft PowerBi [Download Here](https://apps.microsoft.com)
  - For Analysis Cleaning and Visualization
  - For Data Visualization and reporting
    
- CSV (Comma Separated Value)  File
  
- SQL (STRUCTURED QUERY LANGUAGE) [Download Here](https://www.microsoft.com)
  - For Data query
    
- GITHUB
  - For documentation AND Portfolio Building  


## EXPLORATORY DATA ANALYSIS:
Exploratory Data Analysis (EDA) involves investigating and summarizing datasets to discover patterns, trends, relationships, and anomalies, often before applying more complex statistical models.
EDA involves graphical and statistical techniques, helping analysts understand the data's underlying structure, spot errors, and gain insights that inform decision-making and further analysis.


## STAGE 1: WORKING WITH DATA ON MICROSOFT EXCEL
At the initial stage of the project, we downloaded the file from CANVAS LMS 
then we went ahead with Data Cleaning, Removing Duplicates value
  - Data cleaning i.e removing Duplicate values - Using this operation in Excel, 40079 duplicate values were removed and 9921 Unique values remained
  - I also calculated TOTAL REVENUE that is Quantity * Unit sold, to determine the total amount of product sold per day

## GENERATING REPORT USING PIVOT TABLE
  Highlight or click on the desired cell within your data range
  Go to the insert Tab, Click on the pivot  table button to open a dialog box
  Select Data Range, Choose where to place the pivot table (a new worksheet or in the existing worksheet)
  Build customize and format the table
  
Summarize Total sales by product and pie chart representation

![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/1A.JPG)
![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/1B.JPG)

 Summarize Total Sales by region and pie chart representation
 
![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/2A.JPG)
![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/2B.JPG)

Summarize Total Sales by Month In 2023 and pie chart representation

![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/3A.JPG)
![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/3B.JPG)

Summarize average sales by Product 

![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/4A.JPG)
![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/4B.JPG)

Average revenue per Region

![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/5A.JPG)

Summarize total revenue per Region

![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/1aded077d9d35a9eb406887866dd32c9dd3ae2ef/5B.JPG)



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

Range: the range of cells to evaluate, in this sense product
Criteria: the condition that must be met (can be any of the 6 products in this analysis)
Average_range: the actual cell to average
=AVERAGEIF(C2:C50001,C49988,H2:H50001)

AVERAGE SALES BY PRODUCT USING EXCEL FUNCTION AVERAGE IF
Percentage Revenue by Region
PERCENTAGE REVENUE BY REGION
Percentage sales by product
SALES PER PRODUCT IN PERCENTAGE

# EXPLORATORY DATA ANALYSIS (WITH SQL)
Convert excel sheet to csv
Remove headers
import the csv to my sql
Ensure to format the the date column into YYY-MM-DD while importing the csv into my SQL

A. Top selling product by total sales value

```
SELECT FROM SALESDATA
SELECT Product, SUM(TotalSales) As TotalSales
FROM orders
GROUP BY TotalSales DESC
LIMIT 1

```
B. Total sales for each product category
```
SELECT Product, SUM(Totalsales) As TotalSales
FROM orders
GROUP BY Product;
```
Number of sales transaction in each region
```
SELECT Region, COUNT(*)As NumberOfTransaction
FROM Orders
GROUP BY Region;
```
4.Total revenue per product

```
SELECT Product, SUM(TotalSales)As TotalRevenue
FROM Orders
GROUP BY Product;
```
5.Monthly sales total for the current year

```
SELECT MONTH(OrderDate)As Month, SUM (TotalSales)As MonthlySales
FROM Orders
WHERE YEAR(OrderDate)=YEAR(CURDATED())
GROUP BY MONTH(OrderDate)
ORDER BY MONTH;
```

Top 5 customer by totalpurchase amount
```
SELECT CustomerID,SUM(TotalSales) As TotalPurchase
FROM orders
GROUP BY CustomerID
ORDER BY TotalPurchase DESC
LIMIT 5;
```

Percentage of total sales contributed by each region
```
SELECT Region,
SUM(TotalSales) As TotalSales,
(SUN(TotalSaless)/(SELECTSUM(TotalSales)FROM orders)*100) As PercentageOfTotalSales
FROM orders
GROUP BY Region;
```
Products with no sale in the last quarter
```
 SELECT Product FROM    Salesdata
WHERE NOT EXISTS (SELECT 1 FROM	SALESDATA
```
	WHERE product = product
	AND Orderdate BETWEEN '2024-01-01' and '2024-12-31'
)
```
D
