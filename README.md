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
      
- Microsoft PowerBi [Download Here](https://apps.microsoft.com)
  - For Analysis Cleaning and Visualization
  - For Data Visualization and reporting
    
- CSV (Comma Separated Value)  File
  
   
- GITHUB
  - For documentation AND Portfolio Building  


## EXPLORATORY DATA ANALYSIS:
Exploratory Data Analysis (EDA) involves investigating and summarizing datasets to discover patterns, trends, relationships, and anomalies, often before applying more complex statistical models.
EDA involves graphical and statistical techniques, helping analysts understand the data's underlying structure, spot errors, and gain insights that inform decision-making and further analysis.


## STAGE 1: WORKING WITH DATA ON MICROSOFT EXCEL
At the initial stage of the project, we downloaded the file from CANVAS LMS 
then we went ahead with Data Cleaning, Removing Duplicates value
  - Data cleaning i.e removing Duplicate values - Using this operation in Excel

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

	WHERE product = product
	AND Orderdate BETWEEN '2024-01-01' and '2024-12-31'
)

```
# EXPLORATORY DATA ANALYSIS (WITH POWER BI)

OVERVIEW OF SALES RECORD

![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/9b2c8a4bf41309caf4ad640d2c7e0ac37731e544/SALES2.JPG) 

OVERVIEW 2 

![Image_alt](https://github.com/Menieleven/MENI-LITA-PROJECT/blob/9b2c8a4bf41309caf4ad640d2c7e0ac37731e544/sales%20data%202.JPG)

### SUMMARY
The image is a sales data project report titled "LITA Data Analysis - Sales Data Project Report." It provides a comprehensive overview of sales data, including various metrics and visualizations. The key metrics highlighted are:

- **Count of Customer ID:** 9,921
- **Sum of Total Revenue:** 2M
- **Average Total:** 2.00K
- **Sum of Quantity:** 68K

The report includes several visualizations:
1. **Sum of Total Revenue by Region:** A bar chart showing revenue distribution across different regions.
   - East: 485,935K
   - North: 387.000K
   - South: 927,820K
   - West: 300,345K

2. **Count of Customer ID by Region:** A bar chart showing the number of customers in each region.
   - East: 2,463
   - North: 2,481
   - South: 2,460
   - West: 2,477

3. **Sum of Total Revenue by Product:** A pie chart showing revenue distribution across different products.
   - Shoes: 613K (30.7%)
   - Shirt: 485K (24.0%)
   - Gloves: 300K (15.0%)
   - Hat: 250K (12.5%)
   - Jacket: 181K (9.0%)
   - Socks: 176K (8.8%)

4. **Count of Region by Region:** A map showing the geographical distribution of regions in Nigeria.

### Conclusion
The sales data analysis reveals several key insights:
1. The East region generates the highest revenue (1.2M) and has a significant number of customers (2,463).
2. The North region follows with 450.75K in revenue and 2,481 customers.
3. The South and West regions have lower revenues and customer counts compared to the East and North.
4. Shoes are the top-selling product, contributing 30.7% to the total revenue, followed by shirts at 24.0%.
5. The least revenue-generating products are socks and jackets, contributing 8.8% and 9.0% respectively.
6. Customer distribution is quite even across all regions, with each region having around 2480 customers.
7. Shoes lead as the top-selling product, contributing 30.6% to the total revenue, followed by shirts at 24.0%. Gloves, hats, jackets, and socks also contribute notably to the overall revenue.

### Recommendations
Based on the analysis, the following recommendations can be made:
1. **Focus on High Revenue Regions:** Increase marketing and sales efforts in the East and North regions to capitalize on their high revenue potential.
2. **Product Strategy:** Given that shoes and shirts are the top revenue-generating products, consider expanding the product line or offering promotions for these items to boost sales further.
3. **Improve Sales in Low Revenue Regions:** Develop targeted strategies to increase sales in the South and West regions, such as localized marketing campaigns or partnerships with local businesses.
4. **Inventory Management:** Ensure adequate inventory levels for high-demand products like shoes and shirts to avoid stockouts and lost sales opportunities.
5. **Customer Engagement:** Implement customer loyalty programs in regions with high customer counts to retain existing customers and attract new ones.

By focusing on these areas, the company can optimize its sales strategy and drive higher revenue growth.


