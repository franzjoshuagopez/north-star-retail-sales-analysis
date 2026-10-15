#Data Dictionary

##fact_sales

| Column | Description | Data Type |
|:---:|:---:|:---:|:---:|
| row_id | row identifier | Number |
| order_id | order identifier | Text |
| order_date | date of order submission | Date |
| ship_date | shipping date | Date |
| ship_mode | shipping mode | Text |
| customer_id | customer identifier | Text |
| sales | sales amount | Currency |
| quantity | product quantity | Number |
| discount | order discount | Descimal |
| profit | order profit | Currency |
| product_key | foreign key for product | Number |
| discount_group | discount grouping | Text |
| discount_group_sorting | sorting key for discount group | Number |

##dim_product

| Column | Description | Data Type |
|:---:|:---:|:---:|:---:|
| product_key | row identifier | Number |
| product_id | product identifier | Text |
| category | product category | Text |
| subcategory | product subcategory | Text |
| product_name | product name | Text |

##dim_customer

| Column | Description | Data Type |
|:---:|:---:|:---:|:---:|
| customer_id | customer identifier | Text |
| customer name | customer name | Text |
| segment | customer segment | Text |
| country | customer country | Text |
| city | customer city | Text |
| state | customer state | Text |
| postal_code | customer postal code | Text |
| region | customer region | Text |

##dim_date

| Column | Description | Data Type |
|:---:|:---:|:---:|:---:|
| date | date range | date |
| year | date year | Number |
| year_quarter | date quarter year | Text |
| quarter | date quarter | Number |
| year_month | date year month | Text |
| month_year | date month year | Text |
| month_number | date month | Number |
| month_name | date month | Text |
| week_number | date week | Number |
| day_number | date day | Number |
| day_name | date day | Text |