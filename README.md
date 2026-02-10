# task_14# ETL Mini Pipeline – Revision Notes

## 1. What is ETL?
ETL stands for:
- **Extract** – Collect data from source (CSV file)
- **Transform** – Clean, modify, and structure data
- **Load** – Store data into database or files

---

## 2. Dataset Used
**Sales Dataset Columns:**
- Transaction ID
- Date
- Customer ID
- Gender
- Age
- Product Category
- Quantity
- Price per Unit
- Total Amount

---

## 3. Extract Phase
- CSV file uploaded to Google Colab
- Data read using `pandas.read_csv()`
- Raw data stored in `raw/raw_data.csv`

---

## 4. Transform Phase
### Data Cleaning
- Removed duplicate records
- Removed null values
- Standardized column names (lowercase, underscores)

### Data Type Conversion
- Date → datetime
- Quantity, Age → integer
- Price, Total Amount → float

### Derived Columns
- `calculated_amount = quantity × price_per_unit`
- `high_value_txn`  
  - 1 if total_amount > 1000  
  - 0 otherwise

### Data Splitting
- **Customers Table** → customer_id, gender, age
- **Orders Table** → transaction_id, date, customer_id, total_amount
- **Products Table** → product_category, price_per_unit

---

## 5. Load Phase
- Transformed data saved as CSV files:
  - customers.csv
  - orders.csv
  - products.csv
- Data loaded into **SQLite database** using `to_sql()`

---

## 6. Validation
- Row count checked before and after cleaning
- Verified calculated amount logic
- Ensured no duplicate customer records

---

## 7. Tools & Technologies Used
- Python
- Pandas
- Google Colab
- SQLite
- CSV files

---

## 8. Key Interview / Exam Points
- ETL improves data quality and usability
- Transformation is the most important step
- SQLite is lightweight and easy for small projects
- Derived columns help in business insights

---

## 9. Conclusion
This ETL pipeline demonstrates how raw sales data can be transformed into structured, analysis-ready data using Python and loaded into a database efficiently.
