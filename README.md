# Olist E-Commerce SQL Analytics Project

## 📌 Project Overview

This project focuses on analyzing the **Olist E-Commerce dataset** using **Microsoft SQL Server**.

The main objective of this project is to perform:

* Data Profiling
* Data Quality Validation
* Data Cleaning
* Exploratory Data Analysis
* Business Analysis

The dataset contains information about customers, orders, products, sellers, payments, reviews, and geolocation.

---

## 🎯 Project Objectives

The main objectives of this project are:

* Understand the structure and quality of the dataset.
* Identify missing and duplicate values.
* Validate data types and relationships between tables.
* Detect invalid or inconsistent data.
* Analyze customer, order, product, seller, and payment data.
* Generate meaningful business insights using SQL.

---

## 🛠️ Tools & Technologies

* **Microsoft SQL Server**
* **SQL Server Management Studio (SSMS)**
* **SQL**
* **CSV Dataset**
* **Git & GitHub**

---

## 📂 Dataset

The project uses the following Olist E-Commerce datasets:

| Dataset                                 | Description                   |
| --------------------------------------- | ----------------------------- |
| `olist_customers_dataset.csv`           | Customer information          |
| `olist_geolocation_dataset.csv`         | Geographic location data      |
| `olist_order_items_dataset.csv`         | Order item details            |
| `olist_order_payments_dataset.csv`      | Payment information           |
| `olist_order_reviews_dataset.csv`       | Customer reviews              |
| `olist_orders_dataset.csv`              | Order information             |
| `olist_products_dataset.csv`            | Product details               |
| `olist_sellers_dataset.csv`             | Seller information            |
| `product_category_name_translation.csv` | Product category translations |

---

## 🗂️ Project Structure

```text
OLIST-E-COMMERCE-SQL-ANALYTICS-PROJECT/
│
├── data/
│   ├── olist_customers_dataset.csv
│   ├── olist_geolocation_dataset.csv
│   ├── olist_order_items_dataset.csv
│   ├── olist_order_payments_dataset.csv
│   ├── olist_order_reviews_dataset.csv
│   ├── olist_orders_dataset.csv
│   ├── olist_products_dataset.csv
│   ├── olist_sellers_dataset.csv
│   └── product_category_name_translation.csv
│
├── sql/
│   ├── data_profiling.sql
│   ├── data_quality_validation.sql
│   └── analysis.sql
│
└── README.md
```

---

# 🔍 Data Profiling

Data profiling is performed to understand the overall structure and characteristics of the dataset.

The following checks are performed:

* Total number of rows
* Total number of columns
* Data types
* NULL or missing values
* Unique values
* Duplicate records
* Minimum and maximum values
* Distribution of important categorical columns

Example:

```sql
SELECT COUNT(*) AS total_rows
FROM customers;
```

---

# ✅ Data Quality Validation

The dataset is validated to identify potential data quality issues.

The following checks are performed:

### 1. Missing Values

```sql
SELECT
    SUM(CASE WHEN customer_id IS NULL THEN 1 ELSE 0 END) AS missing_customer_id,
    SUM(CASE WHEN customer_city IS NULL THEN 1 ELSE 0 END) AS missing_city
FROM customers;
```

### 2. Duplicate Records

```sql
SELECT
    customer_id,
    COUNT(*) AS duplicate_count
FROM customers
GROUP BY customer_id
HAVING COUNT(*) > 1;
```

### 3. Invalid Values

Example validation for order items:

```sql
SELECT *
FROM order_items
WHERE price <= 0
   OR freight_value < 0;
```

### 4. Invalid Review Scores

```sql
SELECT *
FROM order_reviews
WHERE review_score NOT BETWEEN 1 AND 5;
```

### 5. Product Dimension Validation

```sql
SELECT *
FROM products
WHERE product_weight_g <= 0
   OR product_length_cm <= 0
   OR product_height_cm <= 0
   OR product_width_cm <= 0;
```

### 6. Date Validation

```sql
SELECT *
FROM orders
WHERE order_delivered_customer_date < order_purchase_timestamp;
```

---

# 📊 Tables Used

The following tables are used for analysis:

* Customers
* Geolocation
* Orders
* Order Items
* Order Payments
* Order Reviews
* Products
* Sellers
* Product Category Translation

---

# 📈 Planned Analysis

The project will explore questions such as:

* Which states have the highest number of customers?
* Which product categories generate the most revenue?
* Who are the top-performing sellers?
* What are the most common payment methods?
* What is the average order value?
* How does delivery time affect customer reviews?
* Which products have the highest number of sales?
* Which states generate the highest revenue?
* What factors influence customer satisfaction?

---

# 🚀 How to Run the Project

1. Clone the repository.

```bash
git clone https://github.com/Shubhamkeshri433/OLIST-E-COMMERCE-SQL-ANALYTICS-PROJECT.git
```

2. Open **SQL Server Management Studio (SSMS)**.

3. Create a new database.

```sql
CREATE DATABASE Olist_Ecommerce;
```

4. Import the CSV datasets into SQL Server.

5. Run the SQL scripts in the following order:

```text
1. data_profiling.sql
2. data_quality_validation.sql
3. analysis.sql
```

---

# 📌 Current Task

The current task is to perform **Data Profiling and Data Quality Validation** on the complete dataset.

The validation process includes checking:

* Missing values
* Duplicate records
* Invalid values
* Incorrect data types
* Date inconsistencies
* Data relationships
* Data completeness

---

# 👨‍💻 Author

**Rishabh Kesari**

Aspiring Data Analyst | SQL | Python | Pandas | Data Analysis

---

## ⭐ If you found this project useful, consider giving it a star!
