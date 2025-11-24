# Data-Analyst-Project
Exploratory data analysis for an online store based in UK.

---

## TL;DR

Quick summary: Revenue growth is flat and the business is highly dependent on a very small set of customers and products. Targeted retention and identification of anonymous buyers are the highest-impact levers.

Key metrics:
- YoY revenue: +1% total; identified-customers revenue: −2.7% YoY.
- Customer headcount: +1% (4264 → 4320); lost 1,526 customers (35.8%) vs 1,582 new customers.
- Revenue concentration: top 2% ≈ 36% of revenue; top 20% > 73%.
- Anonymous transactions: 24.5% of transactions in Year 2 (revenue share ≈ 15.1%); anonymous AOV £1,032.50 (vs Elite £931.20).
- SKU concentration: top 5% SKUs ≈ 45.5% of revenue.

Business ask: Prioritize targeted retention for high-value cohorts, convert anonymous buyers into identified customers, and improve data quality to enable measurement and personalization.

---

## Table of Contents

1. Background & Overview
2. Data structure overview (short)
3. Executive summary (WHAT / Business objective)
4. Insight Deep Dive — WHAT (key findings) + WHY (drivers / root causes)
5. Methodology / How to reproduce / Limitations / Metric definitions
6. Recommendations (short action summary + link to Recommendation.md)
7. Additional files & artifacts

---

## 1. Background and Overview
This project analyses two years of transaction-level data from a UK-based online retailer (gifts & home decoration). The goal is to surface business-critical findings and propose targeted, measurable actions to improve retention, increase customer lifetime value, and reduce revenue risk.

Dataset scope: two-year transaction history (item-level: invoice, SKU, qty, unit price, customer identifier, timestamp, country). [See Data Structure Overview below.]

---

## 2. Data Structure Overview
The dataset comprises two years of transactional records from the online retail store (December 1, 2009 – December 19, 2011). Core fields: InvoiceNo, StockCode (SKU), Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country.

Recommended additions (in pipeline): discount flag, normalized customer contact fields, promo table, canonical product master, cancellation linkage via standardized invoice IDs.

---

## 3. Executive Summary
The dataset originates from an online retail store based in the United Kingdom that specializes in gifts and home decoration products. The analysis covers two years of transaction records, from December 2009 to November 2011, including detailed information on products, transaction dates, quantities, pricing, and customer identifiers. For comparison purposes, the dataset is divided into two periods:
- Year 1: December 1, 2009 – November 30, 2010
- Year 2: December 1, 2010 – November 30, 2011

Business objective: Enable targeted and resource-efficient customer retention and value-growth strategies by delivering reliable customer segmentation (value + behavioral), converting high-AOV anonymous buyers into identified customers, and creating measurement-ready campaigns.

### Key segment metrics (Year‑2 snapshot)
High-level result: Minimal year-over-year growth masks a decline in value among identified customers and the loss of many high-value accounts. Segmentation and data improvements are required to direct retention spend efficiently.
Year‑2 segment snapshot: (summary table / key numbers)

| Segment     | Y2 Customer Count | Y2 Recency | Y2 Frequency | Y2 Monetary            | Avg Order Value          | Revenue Share | %Have Cancellations |
| ----------- | ----------------- | ---------- | ------------ | ---------------------- | ------------------------ | ------------- | ------------------- |
| VIP         | 16                | 8.31       | 57.94        |  £  102,108.13         |  £         1,996.89      | 21%           | 94%                 |
| Elite       | 70                | 12.86      | 26.84        |  £     17,968.54       |  £            931.20     | 16%           | 90%                 |
| Premium     | 771               | 32.78      | 8.79         |  £       3,751.20      |  £            506.53     | 37%           | 80%                 |
| Mass        | 3456              | 105.27     | 2.31         |  £          602.84     |  £            260.09     | 26%           | 38%                 |
| Hibernating | 1533              | 496.85     | 0            |  £                   - |  £                     - | 0%            | 23%                 |

To view the full customer, product, and segment metric tables, download the following file:
[metrics_overview_full.md](./metrics_overview_full.md.xlsx)

---

## 4. Insight Deep Dive — WHAT (Key findings) + WHY (Drivers & root causes)


### 4.1 Revenue & customer concentration

Takeaway: Revenue is highly concentrated—small customer cohorts drive most revenue; retention of these cohorts is critical.

- Total Revenue rose slightly (+1%) but identified-customer revenue fell ~2.7%.
- On each year, Top 2% ≈ 36% of revenue; top5% > 48% top 20% > 73%; bottom 50% ≈ 8%.
<img width="623" height="464" alt="CustomerPareto" src="https://github.com/user-attachments/assets/f4c351fd-1abc-4686-8203-af1926c44a37" />
Caption: show share of revenue by top X% and mark top-2% and top-20%.

### 4.2 Churn / cohort revenue impact

Takeaway: Net headcount masks an erosion of cohort value — losing high-value customers drove revenue decline.

- Lost 1,526 customers (35.8%) and acquired 1,582 new customers;  many of the churned customers were high-value (76 from prior Year 1 top 20%, 5 from top 2%).
- Although new customers generated revenue (~£1,350k), identified-customer revenue declined ~2.7% YoY; retained customers (customer with transactions in both periods) spent ~8% less in Year 2, and Year 1 top-20% spent ~13.76% less.

<img width="627" height="280" alt="RevenueWaterfall" src="https://github.com/user-attachments/assets/0dec4c6e-8e7a-4e5e-86b1-bcf958cb4618" />

### 4.3 Anonymous (non-identified) customers

Takeaway: Rising anonymous share is a missed growth & measurement opportunity.

- Anonymous transactions ↑ 24.5% of transactions (Year 2); revenue share ≈ 15.14%.
- Anonymous AOV (£1,032.50) > Elite AOV (£931.20).

<img width="850" height="169" alt="image" src="https://github.com/user-attachments/assets/e7947317-c3e5-4f0e-a404-c083750c8a44" />

### 4.4 Seasonality & buyer heterogeneity

Takeaway: Fall (Nov) spike suggests seasonal playbook; wholesaler behaviors distort simple RFM.

- Fall ≈ 36.9% revenue, November peak; wholesalers show diverse frequency patterns that reduce RFM effectiveness.
- Implication: Use behavior-aware segmentation (wholesale vs retail; seasonal buyers) rather than plain RFM.
<img width="627" height="309" alt="RevenueSeasonal" src="https://github.com/user-attachments/assets/0edf021a-6caf-4de8-ad45-3c1184d2258d" />

### 4.5 Product concentration & SKU risk

Takeaway: Product portfolio is as concentrated as the customer base — SKU risk is significant.

- 4,737 SKUs sold; top 5% SKUs ≈ 45.5% revenue; top 20% ≈ 78%.
- SKU Pareto and list of Top-20 SKUs with revenue share.

<img width="623" height="463" alt="ProductPareto" src="https://github.com/user-attachments/assets/2cd9a7f1-1a42-4061-8f98-15c15cd8675a" />

### 4.6 Promo & cancellation signals

Takeaway: Promo usage is limited and uneven; cancellations are common but not the primary churn driver.

- Only 55 customers had recorded discounted transactions — low promotional coverage.

<img width="627" height="343" alt="DiscountChart" src="https://github.com/user-attachments/assets/a19c0658-bc9d-4b3d-9148-b65d8ba94692" />

- Cancellation rates high across segments (e.g., VIP ~94% have at least one cancellation). Cancellation revenue largely concentrated in customers with stable revenue histories — suggests cancellations are not the main churn cause.

<img width="627" height="376" alt="CancellationStackedBarChart" src="https://github.com/user-attachments/assets/8a722d25-8fbd-49e5-8b04-1e5f40b25816" />

- Conclusion: Churn appears more strongly associated with discount-usage patterns, while cancellations contribute little to explaining customer attrition.

### 4.7 Segment-Specific Behavioral Insight (Hibernating Customers)

Takeaway: Value concentration follows product tier: high-value segments buy Top items, low-engagement segments stay in low-tier categories. This gap signals an opportunity to shift low-tier customers upward through targeted Top-product trials.

- Hibernating customers consistently spend on Bottom-tier products throughout Year 1.
- “Unknown” frequency customers (<5 purchases) concentrate spending in Mid and Bottom tiers.
- Premium, Elite, and VIP customers allocate most of their spend to Top-tier products, showing clear value segmentation.

“To explore spending patterns by product category across segments, statuses, and frequency behaviors, download the interactive Power BI file: [InteractiveCharts.pbix](./InteractiveChart.pbix).”

---

## 5. Recommendations (short action summary)

Action summary (top priorities):

1. Protect and grow top cohorts — targeted retention campaigns for top‑20%. Use holdout tests and measure incremental LTV.
2. Convert anonymous buyers — low-friction capture (email/receipt, registration incentives) to unlock targeted marketing.
3. Data & pipeline fixes — canonical product & customer masters, discount flag, cancellation linking, ETL dedupe & identifier normalization.
4. Behavior-aware segmentation — separate wholesalers and seasonal buyers; use product propensity for offer targeting.

Full recommendations and campaign playbook are in [RECOMMENDATION_SHEET.md](./RECOMMENDATION_SHEET.md) (detailed campaign table + sample offers + KPIs).

---

## 6. Methodology / How to reproduce / Limitations / Metric definitions
- Repro environment: notebooks in /notebooks (Jupyter / Colab) — replace with ["Tools used"].
- How to reproduce: run notebooks/00_data_prep.ipynb → 01_segmentation.ipynb → 02_insights.ipynb (or run the provided pipeline). See requirements.txt / environment.yml for package list. [Replace placeholder with actual files/tools].

---

## 7. Caveats and Assumptions
- The dataset does not include profit or cost-of-goods information. Revenue is therefore used as a proxy metric for value contribution throughout the analysis.
- Several SKUs show inconsistent UnitPrice values without corresponding date differences. Although this may reflect undocumented promotions or pricing adjustments, the dataset lacks fields that clarify the cause, making it difficult to attribute price variation accurately.
- No fields or documentation indicating marketing campaigns, discounts, or active promotions are included in the data. For that reason, the analysis assumes the absence of structured promotional activity unless explicitly recorded as a discount.
- Product information is limited to the Description field. Due to missing product attributes or categorization metadata, product classification relies on inferred groupings, which may omit or misclassify certain SKUs.
- Invoice numbers prefixed with “C” consistently contain negative quantities but no explanatory metadata. These entries are therefore treated as cancellation/return transactions.

---

## 8. Additional files & artifacts
- Recommendation.md — detailed campaign and measurement playbook.
- /notebooks — reproducible analysis (notebooks) — [placeholder: add actual notebook filenames].
- InteractiveChart.pbix — Power BI dashboard (links to downloadable file). Note: embedding interactive .pbix inside .md is not supported — provide a downloadable link or publish to Power BI Service and link.

