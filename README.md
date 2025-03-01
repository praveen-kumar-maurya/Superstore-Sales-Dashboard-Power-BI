# Superstore-Sales-Dashboard-Power-BI

# **Dataset Link**
https://www.kaggle.com/datasets/vivek468/superstore-dataset-final

# **Dataset Information**
Row ID => Unique ID for each row,
Order ID => Order ID for each Order,
Order Date => Order Date of the product,
Ship Mode => Shipping Mode specified by the Customer,
Customer ID => Unique ID to identify each Customer,
Customer Name => Name of the Customer,
Segment => The segment where the Customer belongs,
Country => Country of residence of the Customer,
City => City of residence of of the Customer,
State => State of residence of the Customer,
Postal Code => Postal Code of every Customer,
Region => Region where the Customer belong,
Product ID => Unique ID of the Product,
Category => Category of the product ordered,
Sub-Category => Sub-Category of the product ordered,
Product Name => Name of the Product,
Sales => Sales of the Product,
Quantity => Quantity of the Product,
Profit => Profit/Loss incurred

# **Problem Statement**

**The superstore sales dashboard analysis aims to provide data-driven insights into sales and profit trends to maximize sales and profitability.**

# **Project summary**

The Superstore sales analysis utilized a dataset sourced from Kaggle. The data was initially denormalized and underwent normalization into three tables: dimCustomer, dimProducts, and factSales. Data cleaning was performed to remove irrelevant columns and correct errors in the date format for some dates in date column. A new dimDate table was created which contained all dates and then additional date-related columns were generated. A measures table was also created to consolidate all measures. Data modeling was performed to establish one-to-many relationships between the factSales table and the dimension tables, resulting in a star schema. The resulting dashboard featured various visualizations including line charts, bar charts, maps, cards, ribbon charts, tables, tool tip, slicers and filters. The superstore sales dashboard analysis project aimed to provide insights into sales and profit trends across product categories, segments, and regions. The analysis revealed peak sales in March, September, and November, driven by tax season, back-to-school demand, and holiday shopping respectively. Technology had the highest sales and profits, followed by Furniture and Office Supplies. The South region had the lowest overall profit, with North Carolina being the worst-performing state. The Consumer segment had the highest sales, followed by Corporate and Home Office. Recommendations were made to maximize sales and profitability through targeted marketing initiatives, product diversification, and customer retention strategies.

# **Business Objective**

Business objective for the superstore sales dashboard is to increase sales and profitability by leveraging data-driven insights to make informed decisions. The dashboard provides a comprehensive view of sales and profit trends across product categories, segments, and regions. By utilizing the insights provided by the dashboard, the superstore aims to achieve sustainable growth and profitability.

# **DAX Expressions used **

DAX Expressions used for the measures created in Measures table are:- 

1. Total sales = SUM(factSales[Sales])
2. YTD Sales = TOTALYTD([Total sales],'dimDate'[Date])
3. LY YTD Sales = COALESCE(CALCULATE([YTD Sales],SAMEPERIODLASTYEAR('dimDate'[Date])),0)
4. YTD sales Growth % = DIVIDE(([YTD Sales]-[LY YTD Sales]),[LY YTD Sales],0)
5. MTD Sales = TOTALMTD([Total sales],'dimDate'[Date])
6. LY MTD Sales = COALESCE(CALCULATE([MTD Sales],SAMEPERIODLASTYEAR('dimDate'[Date])),0)

YTD sales mean Year-to-date sales, LY YTD Sales mean Last Year-to-date sales, MTD Sales Month-to-date sales, and LY MTD Sales Last Year Month-to-date sales.


DAX Expressions used for creating columns in Date table are:- 

1. dimDate = CALENDAR(MIN(factSales[Order Date]),MAX(factSales[Order Date]))
2. Year = YEAR('dimDate'[Date])
3. Month year = FORMAT('dimDate'[Date],"MMM-YY")
4. Start of year = STARTOFYEAR('dimDate'[Date])
5. Qtr no = QUOTIENT(DATEDIFF('dimDate'[Start of year],'dimDate'[Date],MONTH),3)+1
6. Qtr = "Q" & 'dimDate'[Qtr no]
7. Month year sort = 
   var my = DATEDIFF(dimDate[Start of year],dimDate[Date],MONTH)+1
   return
   if (my<10,dimDate[Fiscal year] & "0"& my,dimDate[Fiscal year] & my)

# **Data Model**
https://github.com/praveen-kumar-maurya/Superstore-Sales-Dashboard-Power-BI/blob/main/Data%20model%20for%20superstore%20sales%20dashboard.PNG
