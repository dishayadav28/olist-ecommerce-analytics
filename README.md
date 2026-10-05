# **Olist E-Commerce Analytics Dashboard**

End-to-end analysis of the Brazilian Olist e-commerce dataset using **PostgreSQL** and **Power BI (DirectQuery)**.

## **Overview**

Analyzes over 100K orders (2016-2018) across sales, products, customers, delivery, reviews, payments and sellers. Raw data is loaded into PostgreSQL, joined and aggregated through SQL views, along DAX measures visualized in a 9-page Power BI report with drill-through.

## **Tech Stack**

PostgreSQL · SQL · Power BI · DAX · DirectQuery

## **Dashboard Pages**

| Page | Focus |
| ----- | ----- |
| Overview | Revenue, orders, customers, AOV, on-time %, rating, YoY |
| Sales Trends | Revenue vs last year, YTD, rolling 30 days, category x year |
| Product & Category | AOV vs orders, top categories, revenue share |
| Customer Geo | Revenue by state and city, state x category |
| Delivery & Logistics | Late orders, delivery days, late % by state |
| Reviews | Rating distribution, late vs on-time ratings |
| Payments | Payment type share, installments, value trends |
| Sellers | Top sellers, revenue per seller, seller state x category |
| Drill Through | Category-level detail page |

## **Key Insights**

* Total revenue of **14.21M** across **98.67K orders**, with an AOV of **144.01**  
* **São Paulo (SP)** is the top state at 5.4M, roughly 38% of revenue  
* **Credit cards** make up \~77% of payment value  
* **93.23%** of orders arrive on time, but late orders average a rating of **2.3** vs **4.2** for on-time ones  
* Late rates vary widely by state, peaking at about 21%

## **Data Model**

Raw tables (olist\_customers\_dataset, olist\_geolocation\_dataset, olist\_products\_dataset, olist\_sellers\_dataset, olist\_orders\_dataset, olist\_order\_items\_dataset, olist\_order\_payments\_dataset, olist\_order\_reviews\_dataset, product\_category\_name\_translation) → indexed → BI views (bi\_fact\_sales plus other optional dimensions) → Power BI via DirectQuery, with an imported DimDate table.

## **How to Run**

1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) and extract the CSVs.  
2. Create a PostgreSQL database (e.g. olist\_db).  
3. Run the scripts in sql/ in order: tables, loading dataset, indexes, views.  
4. Open the .pbix in Power BI Desktop and update the PostgreSQL connection.  
5. Build relationships (if using separate dims) \+ confirm storage mode is DirectQuery.  
6. Create DAX measures (Revenue, Orders, Customers, AOV, YoY, On-time %, Rating, etc.).  
7. Create report pages (Overview, Sales, Products, Customers, Logistics, Reviews, Payments, Sellers).

## **Dataset**

[Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (CC BY-NC-SA 4.0). Currency is Brazilian Real (BRL). Raw data is not included in this repo.

