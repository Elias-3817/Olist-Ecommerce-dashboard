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

![merged_tables](./documentation/Snapshots\Merging tables.png)

## 2. Column Cleanup
Removed unnecessary or duplicate columns, such as IDs already present in other merged tables or metadata columns not needed for analysis.
Renamed columns for clarity eg:

freight_value -> Shipping Cost

product_category_name -> Categories (Original)


## 3. Null Handling
Dropped rows where order_status = "canceled" or order_status = "unavailable" as these rows caused null values in downstream columns.
Other nulls were minimal and were removed to enhance dashboard performance.

## 4. Product Category Translation
Some product_category_name entries were untranslated or inconsistent.
Built a small mapping table with:
Column A: Unique category names

Column B: renamed to meaningful category names

e.g. fashion_underwear_beach → Swimwear

![cleaned_category names](.documetation/SnapshotsProduct_Categories_subtable.png)

Used VLOOKUP-style merge to replace original category names with final labels.

![Vlookup to rename categories](.documentation/Vlookup_to_rename_categories.png)

## 5. Feature Engineering
- Created new and more insightful features.
### 🚚 i.) Delivery Metrics
Delivery Delay: actual_delivery_date - estimated_delivery_date

Delivery Days: actual_delivery_date - shipping_date

### 💰 ii.) Value Metrics
Total_Price_Cost: price + shipping_cost

### 🕒 iii.) Time-based Features
Purchase Year

Purchase Month

Purchase Quarter

Purchase Day of Week

Purchase Hour

These were extracted from the Purchase_Timestamp column using Excel's date functions to enable time-series and behavioral analysis.

![Time based Features](.documentation/Time_Based_Features.png)

### 🧺 iv.) Additional useful buckets
-Used a pivot table to categorize states based on percentiles into tiers according to the revenues generated

![State Pivot table](.documentation/State_Pivot_Table.png)

-Also added order value bucket

✅ Final Dataset Overview
After preprocessing:

- 96K rows and 32 columns
No significant nulls remaining

Clean column names and well-translated categorical data.

Engineered metrics ready for further modeling and dashboard design.

 Summary
The preprocessing phase ensured the dataset was clean, reliable, and structured for analysis. This step was essential to create a solid foundation for the dashboard and insights.

- Snapshots of before and after cleanup
![Before](/documentation/Snapshots/Before_Cleanup.png)

- After
![After](/documentation/Snapshots/After_Cleanup.png)