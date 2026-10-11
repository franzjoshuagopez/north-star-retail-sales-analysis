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