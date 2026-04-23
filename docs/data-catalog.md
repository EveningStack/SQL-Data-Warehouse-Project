# 📊 Gold Layer Data Catalog

## Overview

The **Gold Layer** represents the business-ready data model designed for analytics and reporting. It is structured into:

- **Dimension tables** (descriptive business entities)
- **Fact tables** (transactional and measurable business events)

---

## 1. 🧑‍🤝‍🧑 `gold.dim_customers`

### Purpose

Stores enriched customer information, including demographic and geographic attributes.

### Columns

| Column Name     | Data Type    | Description                                                                     |
| --------------- | ------------ | ------------------------------------------------------------------------------- |
| customer_key    | INT          | Surrogate key uniquely identifying each customer record in the dimension table. |
| customer_id     | INT          | Natural unique identifier assigned to each customer.                            |
| customer_number | NVARCHAR(50) | Alphanumeric reference used for tracking and integration purposes.              |
| first_name      | NVARCHAR(50) | Customer’s first name as recorded in the source system.                         |
| last_name       | NVARCHAR(50) | Customer’s last (family) name.                                                  |
| country         | NVARCHAR(50) | Country of residence (e.g., Australia).                                         |
| marital_status  | NVARCHAR(50) | Marital status (e.g., Married, Single).                                         |
| gender          | NVARCHAR(50) | Gender of the customer (e.g., Male, Female, n/a).                               |
| birthdate       | DATE         | Date of birth (format: YYYY-MM-DD, e.g., 1971-10-06).                           |
| create_date     | DATE         | Timestamp indicating when the customer record was created.                      |

---

## 2. 📦 `gold.dim_products`

### Purpose

Contains product-related attributes and classification details.

### Columns

| Column Name          | Data Type    | Description                                                  |
| -------------------- | ------------ | ------------------------------------------------------------ |
| product_key          | INT          | Surrogate key uniquely identifying each product record.      |
| product_id           | INT          | Natural identifier for the product in source systems.        |
| product_number       | NVARCHAR(50) | Alphanumeric product code used for tracking and inventory.   |
| product_name         | NVARCHAR(50) | Descriptive product name, including type or variant details. |
| category_id          | NVARCHAR(50) | Identifier for the product category grouping.                |
| category             | NVARCHAR(50) | High-level product classification (e.g., Bikes, Components). |
| subcategory          | NVARCHAR(50) | More detailed classification within a category.              |
| maintenance_required | NVARCHAR(50) | Indicates whether maintenance is required (Yes/No).          |
| cost                 | INT          | Base cost of the product in whole currency units.            |
| product_line         | NVARCHAR(50) | Product line or series (e.g., Road, Mountain).               |
| start_date           | DATE         | Date when the product became available for sale.             |

---

## 3. 💰 `gold.fact_sales`

### Purpose

Stores transactional sales data for analytical reporting and performance tracking.

### Columns

| Column Name   | Data Type    | Description                                             |
| ------------- | ------------ | ------------------------------------------------------- |
| order_number  | NVARCHAR(50) | Unique identifier for each sales order (e.g., SO54496). |
| product_key   | INT          | Foreign key referencing `gold.dim_products`.            |
| customer_key  | INT          | Foreign key referencing `gold.dim_customers`.           |
| order_date    | DATE         | Date when the order was placed.                         |
| shipping_date | DATE         | Date when the order was shipped.                        |
| due_date      | DATE         | Payment due date for the order.                         |
| sales_amount  | INT          | Total monetary value of the line item.                  |
| quantity      | INT          | Number of units purchased in the order line.            |
| price         | INT          | Unit price of the product for the transaction.          |

---
