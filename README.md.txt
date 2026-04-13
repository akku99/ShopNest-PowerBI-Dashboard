# 📊 ShopNest Store Analytics Dashboard (Power BI)

## 🚀 Project Overview
This project presents a comprehensive Power BI dashboard built on a retail e-commerce dataset. The goal is to derive actionable insights related to sales performance, delivery efficiency, customer behavior, and product satisfaction.

The dashboard integrates multiple datasets and applies data modeling, DAX calculations, and interactive visualizations to support business decision-making.

---

## 🧩 Dataset Description
The project uses multiple datasets including:

- Customers
- Orders
- Order Items
- Payments
- Reviews
- Products
- Sellers
- Geolocation
- Product Categories

These datasets are connected using a **star schema model** with Orders as the central fact table.

---

## 🏗️ Data Model
- Fact Table: Orders
- Dimension Tables: Customers, Products, Sellers, Payments, Reviews

Relationships:
- Customers → Orders
- Orders → Order Items → Products
- Orders → Payments
- Orders → Reviews

---

## 📊 Key Features & Analysis

### 1. Top Categories by Sales
- Identified top 10 product categories contributing to total revenue.

### 2. Delayed Orders Analysis
- Analyzed delayed deliveries where actual delivery exceeded estimated date.

### 3. Monthly Delivery Performance
- Compared delayed vs on-time orders across months.

### 4. Payment Method Analysis
- Visualized most frequently used payment methods.

### 5. Product Rating Analysis
- Identified top 10 highest-rated and bottom 10 lowest-rated products.

### 6. State-wise Sales Analysis
- Mapped revenue distribution across regions.

### 7. Seasonal Sales Trends
- Analyzed monthly and quarterly sales patterns.

### 8. Revenue Analysis
- Evaluated yearly revenue trends and growth patterns.

---

## 🧮 Key DAX Measures

```DAX
Total Revenue = SUM(order_payments_dataset[payment_value])

Total Orders = DISTINCTCOUNT(orders_dataset[order_id])

Delayed Orders =
CALCULATE(
    COUNTROWS(orders_dataset),
    orders_dataset[order_delivered_customer_date] > orders_dataset[order_estimated_delivery_date]
)

On Time Orders =
CALCULATE(
    COUNTROWS(orders_dataset),
    orders_dataset[order_delivered_customer_date] <= orders_dataset[order_estimated_delivery_date]
)

Avg Rating = AVERAGE(order_reviews_dataset[review_score])

Delay % = DIVIDE([Delayed Orders], [Total Orders])