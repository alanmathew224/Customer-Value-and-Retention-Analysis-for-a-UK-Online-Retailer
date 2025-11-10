# Data-Analyst-Project
Exploratory data analysis for an online store based in UK.

## 1. Background and Overview
This project analyzes two years of transaction data from an online retail store to identify key business issues and uncover their root causes. The objective is to derive insights that can inform strategic recommendations aimed at resolving existing challenges and preventing similar issues from occurring in the future.

## 2. Data Structure Overview
The dataset comprises two years of transactional records from the online retail store (December 1, 2009 – December 19, 2011). It includes item-level sales data with associated customer identifiers, providing a basis for customer-level and product-level analysis. The key fields are as follows:

InvoiceNo — Transaction identifier at the invoice level.

StockCode (SKU) — Unique product-level identifier used for inventory tracking.

Description — Text label describing the product.

Quantity — Number of units purchased in the transaction line.

InvoiceDate — Timestamp capturing the exact date and time of purchase.

UnitPrice — Price per unit of the product at the time of sale.

CustomerID — Encoded customer identifier enabling longitudinal customer tracking.

Country — Geographic location of the customer.

This structure allows for multi-dimensional analysis, including cohort tracking, sales trend evaluation, customer lifetime value estimation, and segmentation based on behavioral and monetary patterns.

## 3. Executive Summary
The dataset originates from an online retail store based in the United Kingdom that specializes in gifts and home decoration products. The analysis covers two years of transaction records, from December 2009 to November 2011, including detailed information on products, transaction dates, quantities, pricing, and customer identifiers. For comparison purposes, the dataset is divided into two periods:

Year 1: December 1, 2009 – November 30, 2010

Year 2: December 1, 2010 – November 30, 2011

The year-over-year comparison shows only a 1% increase in total sales revenue and a 1% increase in the number of customers, indicating stagnant growth. When focusing exclusively on identified customers, revenue declined by 2% in the second year. Additionally, the store lost 1,526 customers (35.78%) while acquiring 1,582 new customers, and a considerable portion of the customers who churned were high-value customers. This highlights that the store is not effectively retaining and developing the value of its customer base.

While various retention and engagement strategies (such as loyalty programs, personalized offers, and improved customer service) could be implemented, their effectiveness depends on whether they are applied to the right customer segments. Therefore, the business objective of this analysis is to enable targeted and resource-efficient customer retention and value-growth strategies by segmenting customers based on their purchasing value and behavioral patterns.

By applying customer segmentation, the store can not only retain high-value customers but also systematically grow customer lifetime value across all segments through more precise, data-driven engagement and revenue optimization initiatives.
