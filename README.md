# Data-Analyst-Project
Exploratory data analysis for an online store based in UK.

## 1. Background and Overview
This project analyzes two years of transaction data from an online retail store to identify key business issues and uncover their root causes. The objective is to derive insights that can inform strategic recommendations aimed at resolving existing challenges and preventing similar issues from occurring in the future.

## 2. Data Structure Overview
The dataset comprises two years of transactional records from the online retail store (December 1, 2009 – December 19, 2011). It includes item-level sales data with associated customer identifiers, providing a basis for customer-level and product-level analysis. The key fields are as follows:

- InvoiceNo — Transaction identifier at the invoice level.

- StockCode (SKU) — Unique product-level identifier used for inventory tracking.

- Description — Text label describing the product.

- Quantity — Number of units purchased in the transaction line.

- InvoiceDate — Timestamp capturing the exact date and time of purchase.

- UnitPrice — Price per unit of the product at the time of sale.

- CustomerID — Encoded customer identifier enabling longitudinal customer tracking.

- Country — Geographic location of the customer.

This structure allows for multi-dimensional analysis, including cohort tracking, sales trend evaluation, customer lifetime value estimation, and segmentation based on behavioral and monetary patterns.

## 3. Executive Summary
The dataset originates from an online retail store based in the United Kingdom that specializes in gifts and home decoration products. The analysis covers two years of transaction records, from December 2009 to November 2011, including detailed information on products, transaction dates, quantities, pricing, and customer identifiers. For comparison purposes, the dataset is divided into two periods:

- Year 1: December 1, 2009 – November 30, 2010

- Year 2: December 1, 2010 – November 30, 2011

The year-over-year comparison shows only a 1% increase in total sales revenue and a 1% increase in the number of customers, indicating stagnant growth. When focusing exclusively on identified customers, revenue declined by 2% in the second year. Additionally, the store lost 1,526 customers (35.78%) while acquiring 1,582 new customers, and a considerable portion of the customers who churned were high-value customers. This highlights that the store is not effectively retaining and developing the value of its customer base.

While various retention and engagement strategies (such as loyalty programs, personalized offers, and improved customer service) could be implemented, their effectiveness depends on whether they are applied to the right customer segments. Therefore, the business objective of this analysis is to enable targeted and resource-efficient customer retention and value-growth strategies by segmenting customers based on their purchasing value and behavioral patterns.

By applying customer segmentation, the store can not only retain high-value customers but also systematically grow customer lifetime value across all segments through more precise, data-driven engagement and revenue optimization initiatives.

## 4. Insight Deep Dive

### WHAT?
#### A. Customer & Revenue Concentration

Headline: Revenue is heavily concentrated in a very small share of customers.

- Top 2% of customers account for ~36% of yearly revenue; top 20% account for >73%, while the bottom 50% contribute only ~8%.

- Overall growth is stagnant: total sales ↑ ~1% YoY and customer count ↑ ~1%, showing little expansion beyond the existing base.

- Business implication: the store’s revenue is highly dependent on a small set of customers—loss or disengagement from these customers creates outsized impact.
<img width="623" height="463" alt="CustomerPareto" src="https://github.com/user-attachments/assets/9d5bc9fd-1d28-4400-9ac3-21c4b976bfaa" />

#### B. Churn, Acquisition & Cohort Revenue Impact

Headline: Net customer churn and cohort-level revenue shifts show value loss despite similar headcount.

- The store lost 1,526 existing customers and acquired 1,582 new customers in Year 2; however, many of the churned customers were high-value (76 from prior Year1 top 20%, 5 from top 2%).

- Although new customers generated revenue (~£1,350k), identified-customer revenue declined ~2.7% YoY; retained customers spent ~8% less in Year 2, and Year1 top-20% spent ~13.76% less (~£768k loss).

- Net effect: headcount stability masks an erosion in customer value—retention (and re-engagement) of high-value cohorts is critical.

<img width="627" height="280" alt="RevenueWaterfall" src="https://github.com/user-attachments/assets/0dec4c6e-8e7a-4e5e-86b1-bcf958cb4618" />

#### C. Anonymous (Non-identified) Customer Impact

Headline: Growing share of anonymous transactions increases revenue uncertainty and limits retention actions.

- Non-identified transactions rose to 24.5% of transactions in Year 2 (from 19.5% in Year 1); their revenue share rose to ~15.14% (from 11.58%).
  
- Anonymous customers in the second year show a 57% higher Average Order Value, reaching £1,032.50, which is higher than the AOV of Elite customers (£931.20). This suggests that anonymity does not equate to low-value behavior; on the contrary, it may represent a missed opportunity for customer identification and targeted nurturing.

- Business implication: reducing anonymous transactions or capturing identifiers will unlock targeted marketing and repeat-purchase strategies.

  <img width="850" height="169" alt="image" src="https://github.com/user-attachments/assets/e7947317-c3e5-4f0e-a404-c083750c8a44" />

#### D. Seasonality & Customer Behavior Patterns

Headline: Strong seasonality (Fall/November peak) and heterogeneous buyer types complicate one-size-fits-all segmentation.

- Fall accounts for ~36.9% of revenue with a November peak; other seasons average ≈21% each, and Fall also shows spikes in customers and transactions.

- Many top customers are wholesalers with diverse buying rhythms (frequent small orders, periodic bulk orders, or seasonal-only purchases).

- Implication: basic RFM alone is insufficient — wholesalers distort frequency/recency signals and require behavior-aware segmentation.

<img width="627" height="309" alt="RevenueSeasonal" src="https://github.com/user-attachments/assets/0edf021a-6caf-4de8-ad45-3c1184d2258d" />

#### E. Product Revenue Concentration & SKU Dependence

Headline: Sales are concentrated in a small subset of SKUs—product portfolio risk mirrors customer concentration.

- 4,737 SKUs sold over two years; top 5% of SKUs generate ~45.5% of revenue, top 20% generate ~78%, bottom 50% only ~4.6%.

- The store is dependent on a narrow product set for revenue—SKU-level failures or stockouts could have large revenue implications.

<img width="623" height="463" alt="ProductPareto" src="https://github.com/user-attachments/assets/2cd9a7f1-1a42-4061-8f98-15c15cd8675a" />

## RESULT

The Year-2 segment metrics show a clear performance gradient across customer tiers. VIPs drive overwhelmingly higher value, marked by extremely frequent purchases, high monetary contribution, broad product variety, and the shortest repurchase cycle. Elite customers follow with strong but substantially lower spend and frequency. Premium buyers maintain moderate purchase activity and product diversity, while Mass customers contribute minimally across all dimensions.

<img width="928" height="121" alt="image" src="https://github.com/user-attachments/assets/34280638-9db5-4651-8ca7-8e85b60d2b6a" />

## WHY?

#### A. Discounting & Promotional Usage

Headline: Discounting is rarely used and concentrated in a few customers; promotional coverage is minimal.

- Only 55 customers used discounts, indicating very limited discount activity. The targeting doesn't appear to have been planned carefully, yet a surprisingly large number of mass customers still received discounts—more than those in the elite segment.

- Low promotional penetration suggests missed opportunities for targeted offers to retain or reactivate specific cohorts.

<img width="627" height="343" alt="DiscountChart" src="https://github.com/user-attachments/assets/a19c0658-bc9d-4b3d-9148-b65d8ba94692" />

#### B. Segment-Specific Behavioral Insight (Hibernating Customers)

Headline: Hibernating customers concentrate spend in low-value categories, potentially explaining churn.

- “Hibernating” cohort spends predominantly on the “Bottom” product category across months in Year 1.

- Customers flagged as having “Unknown” frequency behavior—those who purchase fewer than five times—allocate most of their spending to Mid-tier and Bottom-tier products.

- In contrast, Premium, Elite, and VIP segments direct the majority of their spending toward Top-tier products, indicating a clear value stratification across behavioral groups.

- Possible interpretation: low-ticket purchasing mix reduces engagement and increases likelihood of churn when product relevance or availability declines.

#### C. Cancellations & Returns — Distribution and Impact

Headline: Cancellations are widespread across segments but do not appear to be the primary driver of customer loss.

- High percentages of cancellations exist across segments (e.g., ~94% of VIPs, 90% of Elites have had at least one cancellation).

<img width="627" height="376" alt="CancellationStackedBarChart" src="https://github.com/user-attachments/assets/8a722d25-8fbd-49e5-8b04-1e5f40b25816" />

- Categorizing cancellation revenue: 71.18% of cancellation revenue loss falls into a “good” group (customers with stable or only slightly declining net revenue), 25.82% in the “bad” group (lost/declining customers), 3% others.

<img width="591" height="504" alt="CancellationPieChart" src="https://github.com/user-attachments/assets/071436d4-5480-49cc-964b-13c4d4eab5e3" />

- Conclusion: cancellations alone are unlikely to explain most customer churn; other factors (value decline, competition, product fit) are likely contributors.
