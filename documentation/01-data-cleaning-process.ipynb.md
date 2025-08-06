## Data Integration Process

### Source Tables
- 8 CSV files from Brazilian Olist e-commerce dataset
![CSV Files](C:\Users\ADMIN\Documents\GitHub\Olist-Ecommerce-dashboard\data\01-raw-data\Raw datasets)

### Key Transformations
1. **Base table:** Merged orders with order items (113k rows)
![Merged datasets](C:\Users\ADMIN\Documents\GitHub\Olist-Ecommerce-dashboard\data\01-raw-data\Merged datasets.png)
2. **Geography:** Added customer and seller locations
3. **Products:** Added categories (Portuguese + English)
![Category English](C:\Users\ADMIN\Documents\GitHub\Olist-Ecommerce-dashboard\data\01-raw-data\Category_English col.png)
4. **Business metrics:** Created delivery_days, total_item_value
![Business Metrics added](C:\Users\ADMIN\Documents\GitHub\Olist-Ecommerce-dashboard\data\01-raw-data\Final table with added columns.png)
5. **Time analysis:** Extracted year/month from timestamps

STEP 1 – Drop useless or duplicate columns  
STEP 2 – Handle nulls / missing data  
STEP 3 – Clean categoricals (city, state, etc.)  
STEP 4 – Date engineering (year, month, weekday, etc.)  
STEP 5 – Recalculate delivery metrics (delivery delay etc.)  
STEP 6 – Price engineering (total price, order bucket)  
STEP 7 – Customer insights (grouped by customer_id)  
STEP 8 – Location grouping (state/city-level performance)  
STEP 9 – Final cleanup + export

### Final Output
- Master table: 35 columns, 113k+ rows
- Ready for Power BI dashboard analysis