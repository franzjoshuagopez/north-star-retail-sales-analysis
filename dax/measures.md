#D AX Measures

## Overview
Below is the list of measures created for this Power BI Dashboard to measure, calculate, and/or analyze the data and provide meaningful charts and insights

## Core Business Measures

### total_sales
- Purpose: calculate the total sales for the dataset using the column sales in fact_sales
- DAX: total_sales = SUM(fact_sales[sales])
- Used for: charts/cards to show total sales

### total_order
- Purpose: calculate the distinct number of orders for the dataset using the column order_id in fact_sales
- DAX: total_order = DISTINCTCOUNT(fact_sales[order_id])
- Used for: charts/cards to show distinct count of orders

### total_profit
- Purpose: calculate the total profit for the dataset using the column profit in fact_sales
- DAX: total_order = total_profit = SUM(fact_sales[profit])
- Used for: charts/cards to show total profit

### total_profit
- Purpose: calculate the total profit for the dataset using the column profit in fact_sales
- DAX: total_order = total_profit = SUM(fact_sales[profit])
- Used for: charts/cards to show total profit

### average_discount
- Purpose: calculate the average discount for the dataset using the column discount in fact_sales
- DAX: total_order = average_discount = AVERAGE(fact_sales[discount])
- Used for: charts to show average discount

### Average Order Value
- Purpose: calculate the average order value for the dataset using the column discount in fact_sales
- DAX: total_order = Average Order Value = DIVIDE([total_sales],[total_order])
- Used for: charts to show average order value

### profit_margin
- Purpose: calculate the profit margin percentage for the dataset using the column discount in fact_sales
- DAX: total_order = profit_margin = DIVIDE([total_profit],[total_sales])
- Used for: charts/cards to show profit margin

## Time Intelligence

### Sales Previous Month
- Purpose: calculate the sales of the previous month
- DAX: total_order = Sales Previous Month = CALCULATE([total_sales],DATEADD(dim_date[date], -1, MONTH))
- Used for: to calculate Month on Month growth percentage

### Sales MoM%
- Purpose: calculate the sales of the previous month in percentage
- DAX: total_order = Sales MoM % = DIVIDE([total_sales] - [Sales Previous Month],[Sales Previous Month])
- Used for: charts to show MoM as tooltip

### Sales Previous Year
- Purpose: calculate the sales of the previous year
- DAX: total_order = Sales Previous Year = CALCULATE([total_sales],DATEADD(dim_date[date], -1, YEAR))
- Used for: to calculate Year on Year growth percentage

### Sales YoY%
- Purpose: calculate the sales of the previous year in percentage
- DAX: total_order = Sales YoY % = DIVIDE([total_sales] - [Sales Previous Year],[Sales Previous Year])
- Used for: charts to show YoY as tooltip

### Profit Previous Month
- Purpose: calculate the profit of the previous month
- DAX: total_order = Profit Previous Month = CALCULATE([total_profit],DATEADD(dim_date[date], -1, MONTH))
- Used for: to calculate Month on Month growth percentage

### Profit MoM%
- Purpose: calculate the profit of the previous month in percentage
- DAX: total_order = Profit MoM % = DIVIDE([total_profit] - [Profit Previous Month],[Profit Previous Month])
- Used for: charts to show MoM as tooltip

### Profit Previous Year
- Purpose: calculate the profit of the previous year
- DAX: total_order = Profit Previous Year = CALCULATE([total_profit],DATEADD(dim_date[date], -1, YEAR))
- Used for: to calculate Year on Year growth

### Profit YoY Change
- Purpose: calculate the profit of the previous year in currency
- DAX: total_order = Profit YoY Change = [total_profit] - [Profit Previous Year]
- Used for: charts to show YoY as tooltip

## Rankings

### Top Profit Segment Name
- Purpose: Determine the highest Customer Segment in profit and return its name
- DAX: Top Profit Segment Name = VAR _top_profit_segment_name =TOPN(1,VALUES(dim_customer[segment]),[total_profit],DESC) RETURN(CONCATENATEX(_top_profit_segment_name,dim_customer[segment],", "))
- Used for: cards to show the segment name with highest profit

### Top Profit Segment Value
- Purpose: Determine the highest Customer Segment in profit and return its value
- DAX: Top Profit Segment Name = Top Profit Segment Value = MAXX(TOPN(1,VALUES(dim_customer[segment]),[total_profit],DESC),[total_profit])
- Used for: cards to show the profit value of the segment with highest profit

### Top Sales Segment Name
- Purpose: Determine the highest Customer Segment in sales and return its name
- DAX: Top Sales Segment Name = VAR _top_sales_segment =TOPN(1,VALUES(dim_customer[segment]),[total_sales],DESC) RETURN(CONCATENATEX(_top_sales_segment,dim_customer[segment],", "))
- Used for: cards to show the segment name with highest sales

### Top Sales Segment Value
- Purpose: Determine the highest Customer Segment in sales and return its value
- DAX: Top Sales Segment Value = MAXX(TOPN(1,VALUES(dim_customer[segment]),[total_sales],DESC),[total_sales])
- Used for: cards to show the sales value of the segment with highest sales

## Diagnostic/Insight Measures

### Furniture Sales
- Purpose: Calculate the sales of the product category Furniture
- DAX: Furniture Sales = CALCULATE([total_sales],dim_product[category] = "Furniture")
- Used for: insights to show value within the text

### Furniture Profit Margin
- Purpose: Calculate the profit margin of the product category Furniture
- DAX: Furniture Profit Margin = CALCULATE([profit_margin],dim_product[category] = "Furniture")
- Used for: insights to show value within the text

### Home Office Customer %
- Purpose: Calculate the percentage of customers for the segment Home Office
- DAX: Home Office Customer % = DIVIDE(CALCULATE(DISTINCTCOUNT(dim_customer[customer_id]),dim_customer[segment] = "Home Office"),CALCULATE(DISTINCTCOUNT(dim_customer[customer_id]),REMOVEFILTERS(dim_customer[segment])))
- Used for: insights to show value within the text

### Home Office Average Order Value
- Purpose: Calculate the average order value for the segment Home Office
- DAX: Home Office Average Order Value = CALCULATE([Average Order Value],dim_customer[segment] = "Home Office")
- Used for: insights to show value within the text

## DAX Concepts Demonstrated
Brief list of concepts used:
- CALCULATE
- DIVIDE
- DATEADD
- TOPN
- MAX/MAXX
- CONCATENATEX
- VALUES
- REMOVEFILTERS
- Filter Context
- Context Iteration
- Iterators



