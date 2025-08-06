# DATA CLEANING PROCESS

-This markdown outlines the data preprocessing steps performed in excel before building visualizations and deriving insights in Power BI. The raw dataset was messy, inconsistent, and spread across multiple tables. Here's how I cleaned and transformed it into  an analysis-ready format.

## 1. Dataset Loading & Table Merging
Imported the following CSV files into Excel via Power Query:

olist_customers_dataset.csv

olist_geolocation_dataset.csv

olist_order_items_dataset.csv

olist_order_payments_dataset.csv

olist_order_reviews_dataset.csv

olist_orders_dataset.csv

olist_products_dataset.csv

olist_product_category_name_translation.csv

Used Power Query to merge the tables based on common keys such as order_id, customer_id, product_id, etc.

I also ensured correct join types to avoid duplication or null rows.

[C:\Users\ADMIN\Documents\GitHub\Olist-Ecommerce-dashboard\documentation\Merging tables.png]

🧹 2. Column Cleanup
Removed unnecessary or duplicate columns, such as IDs already present in other merged tables or metadata columns not needed for analysis.

Renamed columns for clarity:

freight_value → Shipping Cost

product_category_name → Product Category (Original)

product_category_name_english → Product Category

🕳️ 3. Null Handling
Dropped rows where order_status = "canceled" or order_status = "unavailable" as these rows caused null values in downstream columns.

Other nulls were minimal and either removed or filled appropriately.

🌐 4. Product Category Translation
Some product_category_name entries were untranslated or inconsistent.

Built a small mapping table with:

Column A: Unique Portuguese category names

Column B: English translations (renamed to meaningful categories)

e.g. fashion_underwear_beach → Swimwear

Used VLOOKUP-style merge to replace original category names with final labels.

📸 [Insert screenshot of the mapping table and merge logic]

📦 5. Feature Engineering
🚚 Delivery Metrics
Delivery Delay: actual_delivery_date - estimated_delivery_date

Delivery Days: actual_delivery_date - shipping_date

💰 Value Metrics
Total Price Value: price + shipping_cost

🕒 Time-based Features
Purchase Year

Purchase Month

Purchase Day of Week

Purchase Hour

These were extracted using Power BI's date functions to enable time-series and behavioral analysis.

📸 [Insert screenshots of calculated columns or DAX logic]

✅ Final Dataset Overview
After preprocessing:

Row count: ~[your number]

No significant nulls remaining

Clean column names and well-translated categorical data

Engineered metrics ready for modeling and dashboards

💡 Summary
The preprocessing phase ensured the dataset was clean, reliable, and structured for analysis. Real-world datasets are rarely plug-and-play — this step was essential to create a solid foundation for the dashboard and insights.