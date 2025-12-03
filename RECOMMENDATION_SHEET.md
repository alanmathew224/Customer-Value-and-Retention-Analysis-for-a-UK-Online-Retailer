# Recommendation — Campaigns & Data & Analytics Pipeline Improvements

> This document contains the detailed recommendations referenced in the **Recommendations** section of `README.md`. It includes:
> 1. Marketing campaign matrix (by segment & status)
> 2. Campaign playbook by behavioral archetype (guideline for offers)
> 3. Data & analytics pipeline improvements (technical requirements)
> 4. Implementation roadmap, measurement framework, and quick wins

---

## 1. Marketing Campaign Recommendation
**Note:** below are two supporting tables. Table A (segment × status) is the operational campaign matrix your marketing team can use directly. Table B contains offer templates by behavioral archetype that act as a short playbook for creative and targeting.

### Table A — Campaign matrix (segment × status)
Columns: **Segment | Status | Objective | Tactic | Channel | Offer example | KPI | Priority**

| Segment     | Status          | Priority | Campaign                  | Tactics                                                                  | Channels                              | Offer Example                                          | Key KPI                                |
| ----------- | --------------- | -------- | ------------------------- | ------------------------------------------------------------------------ | ------------------------------------- | ------------------------------------------------------ | -------------------------------------- |
| VIP         | Active          | Highest  | Loyalty & Expansion       | Cross-sell recs, loyalty boosts, referral incentives                     | Account Manager, Email, Phone, Events | Exclusive 1:1 offers, early access, tailored pricing   | Retention rate, Rev change, Attendance |
| VIP         | At Risk         | Highest  | Winback (High-touch)      | Personalized outreach, special offers, feedback survey                   | Account Manager, Email, Phone, Events | Exclusive 1:1 offers, early access, tailored pricing   | Retention rate, Rev change, Attendance |
| Elite       | Potential       | High     | Expansion & Upsell        | [Elite Active], expansion upsell, cross-sell recs                        | Email, SMS, Phone outreach            | Premium discount, loyalty points, personalized bundles | Rev uplift, Repeat rate                |
| Elite       | Active          | High     | Loyalty & Expansion       | Loyalty boosts, referral incentives                                      | Email, SMS, Phone outreach            | Premium discount, loyalty points, personalized bundles | Rev uplift, Repeat rate                |
| Elite       | At Risk         | High     | Winback (High-touch)      | [Elite Active], personalized outreach, special offers, feedback survey   | Email, SMS, Phone outreach            | Premium discount, loyalty points, personalized bundles | Rev uplift, Repeat rate                |
| Premium     | Potential       | High     | Expansion & Upsell        | [Premium Active] expansion upsell, cross-sell recs                       | Email, Push, Social                   | Category discount, cross-sell                          | Conversion rate, AOV                   |
| Premium     | Active          | Medium   | Loyalty & Expansion       | Loyalty boosts                                                           | Email, Push, Social                   | Category discount, cross-sell                          | Conversion rate, AOV                   |
| Premium     | New             | Medium   | Onboarding & Expansion    | Welcome series, quick-start guides, first-purchase incentives            | Email, Push, Social                   | Category discount, cross-sell                          | Conversion rate, AOV                   |
| Premium     | At Risk         | High     | Winback (High-touch)      | [Premium Active], personalized outreach, special offers, feedback survey | Email, Push, Social                   | Category discount, cross-sell                          | Conversion rate, AOV                   |
| Mass        | Potential       | Medium   | Upsell                    | Cross-sell recs, product bundles, limited-time offers                    | Email, Push, Social                   | Category discount, cross-sell                          | Conversion rate, AOV                   |
| Mass        | Active          | Low      | Loyalty & Expansion       | Loyalty boosts                                                           | Email, Ads, Push                      | Volume discounts, coupons                              | Activation, CAC                        |
| Mass        | New             | Low      | Onboarding                | Welcome series, quick-start guides, first-purchase incentives            | Email, Ads, Push                      | Volume discounts, coupons                              | Activation, CAC                        |
| Mass        | At Risk         | High     | Winback (High-touch)      | Personalized outreach, special offers, feedback survey                   | Email, Ads, SMS, Push                 | Volume discounts, coupons                              | Activation, CAC                        |
| Hibernating | At Risk         | Medium   | Winback (High-touch)      | Personalized outreach, special offers, feedback survey                   | Email, Ads, SMS, Push                 | Volume discounts, coupons                              | Activation, CAC                        |
| Hibernating | Can't Lose Them | Medium   | Save & Retain             | Custom offers, contract-like incentives                                  | Email, Ads, Push                      | Volume discounts, coupons                              | Activation, CAC                        |
| Hibernating | Hibernating     | Low      | Re-activation (low-touch) | Re-engagement emails, seasonal promos                                    | Email, Ads, Push                      | Volume discounts, coupons                              | Activation, CAC                        |
| Anonymous   | Any             | High     | Capture identity          | Incentivized identity capture at checkout                                | Checkout modal, email-on-receipt      | 10% off next order for sign-up                         | % converted to identified, LTV         |


### Table B — Campaign playbook: behavior-based offers
Columns: **Behavior | Objective | Offer type / messaging | Timing | KPI**

| Behavior                | Tactics                                                                                      |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| Seasonal Buyer          | Seasonal promos timed to peak season, timed reminders, limited collections, targeted bundles |
| One-off Buyer           | Discounts on second purchase, retargeting, product education, small repeat incentives        |
| Repetitive Buyer        | Bundle promotions, replenishment reminders, cross-sell complementary items, upsell           |
| Low Frequency Buyer     | Nudge campaigns, limited-time discounts, content to increase relevance                       |
| Reguler Frequency Buyer | Loyalty point accelerators, personalized recommendations                                     |
| High Frequency Buyer    | Exclusive offers, higher-tier loyalty benefits                                               |

### Other campaign guidelines
### A. Seasonality Campaigns — Fall Peak Playbook
**Objective:** Maximize margin and long‑term customer value during the Fall revenue peak while avoiding unnecessary margin erosion.

**Why:** Fall (with a November peak) generates a disproportionate share of annual revenue. The period is ideal for strategic upsell, acquisition, and reactivation—but blanket discounts can damage margin and train customers to buy only on sale.

**Promotions framework:**

* Prefer **tiered incentives** (free‑shipping thresholds, bundle pricing, gift-with-purchase, loyalty points multiplier) over broad percentage-off sitewide sales.
* Use **time-limited, audience-targeted offers**: high-value exclusive offers for VIP/Elite, upgrade bundles for Unknown/Hibernating cohorts, and welcome bundles for new customers.
* Avoid blanket discounts on Top SKUs; instead, use value-preserving mechanics (e.g., bundle Top + Mid with small discount, coupon for a subsequent purchase).

**Tactics (examples):**

* **VIP/Elite:** Early access + curated bundles (limited quantity) — experiment with small exclusive discounts vs. bundled value.
* **New customers:** Welcome bundle featuring a Top product + free shipping threshold.
* **Hibernating / Unknown:** Targeted limited-time upgrade offers (Mid → Top trial bundle) delivered pre‑Fall and during Fall peak.

**Measurement & experiments:**

* Use **holdout groups** (randomized sample or geographies) to measure incremental revenue and LTV.
* Primary KPIs: incremental revenue vs baseline, margin impact, uplift in Top-product penetration, and campaign ROI.
* Secondary KPIs: reactivation rate, AOV, repeat rate at 30/90 days.

**Recommendation on timing:**

* Run a short **pre-Fall test** (2–4 weeks) to validate messaging and mechanics, then scale successful treatments into the main Fall window.
* Maintain a small control group throughout Fall to measure true incremental lift.

### B. Product-level Growth Levers — Top-product Promotion Playbook
**Objective:** Increase high-value revenue by promoting Top products to cohorts with the highest propensity to purchase at higher AOV (e.g., New customers, Premium segments, and targeted Unknown-frequency cohorts).

**Why:** Revenue is concentrated in a small set of SKUs. Efficiently promoting Top products to the right cohorts increases conversion efficiency and AOV without broad margin erosion.

**Tactics:**

* **Top-product trial bundles** for New customers and Unknown-frequency customers: smaller-priced entry bundle featuring a Top SKU + complementary Mid SKU to lower friction and increase attach rates.
* **Personalized cross-sell:** Recommend Top items in post-purchase emails for customers whose purchase history indicates affinity to related categories.

**Measurement & KPIs:**

* Top-product penetration (share of customers who purchase Top SKU) by cohort.
* AOV change and attach rate for cross-sell items.
* Conversion lift on welcome bundles and trial offers (measured vs. matched control group).
* Incremental margin contribution per campaign.

**Example experiment design:**

* Randomly assign new customers into: (A) welcome bundle with Top SKU, (B) standard welcome coupon, (C) control (no incentive). Compare 30‑day repeat rate, AOV, and margin uplift.

**Operational notes:**

* Use the `product_master` and `promotion_master` tables (Recommendation.md) to ensure consistent treatment mapping and attribution.
* Ensure promotional mechanics are recorded at transaction-level (`promo_id`, `discount_amount`) so measurement is deterministic.

## 2. Data & Analytics Pipeline Improvements — Requirements & Rationale
**Goal:** make targeting, attribution, experiment measurement, and personalization reliable and reproducible.

### Required changes (short, business‑facing descriptions)
- **Add `discount_flag` to transactions.** Rationale: enable tracking of discount behaviour, promo attribution, and discount-driven margin analysis.
- **Standardise cancel/return invoice linkage.** All cancellation invoices must reuse the original invoice number prefixed with `C` (e.g., `12345` → `C12345`). Rationale: deterministic join between sale and return for accurate net revenue and churn analysis.
- **Create canonical `product` master.** Columns: `product_id` (StockCode), `name`, `product_category` (tier: Top/Mid/Bottom), `specs`, `date_added`, `current_price`, `price_before`, `price_change_date`. Rationale: avoid duplicate SKUs, support price-history analyses, and enable product-level propensity models.
- **Create canonical `customer` master.** Columns: `customer_id`, `email` (normalized), `name`, `country`, `date_joined`, `lifecycle_status`, `segment`, `source_channel`. Rationale: unified identity for segmentation, personalization, and LTV modeling.
- **Promotion table (`promotion_master`).** Columns: `promo_id`, `start_date`, `end_date`, `type`, `target_segment`, `mechanic`, `notes`. Rationale: canonical source of campaign truth for attribution and ROI.
- **ETL / CDC step for deduplication and normalization.** Include: email normalization, cookie/device-to-customer mapping, and anomalous-row flagging. Rationale: improve matching, reduce false-positives in churn/retention metrics.

### Additional suggested improvements (ops & governance)
- **Promo attribution fields in transactions:** store `promo_id`, `promo_applied`, `discount_amount`, `discount_percent` for each transaction.
- **Price history table** to capture all price changes with effective dates.
- **Automated data-quality checks & alerts** (missing customer IDs, duplicate invoices, price outliers). Set SLAs on data freshness and error rates.
- **Schema versioning & documentation (ERD / DSM).** Maintain a single source-of-truth data model (ERD) and publish to a data catalog.
- **Campaign & experiment tracking schema.** Log campaign IDs, audience snapshot, holdout flag, and campaign exposure to measure incremental lift.
- **Access & ownership:** assign clear owners (Data Engineering, Analytics, Marketing Ops) and delivery timeline for each artifact.

---

## 3. Implementation roadmap & quick wins
**Principles:** prioritize low-effort, high-impact items first (quick wins), then foundational data engineering work.

**Quarter 0 (Quick wins — 2–6 weeks):**
- Add `discount_flag` and `promo_id` to the transaction ingestion.  
- Standardize cancellation invoice pattern (`C` prefix).  
- Launch a 4–6 week identity-capture pilot at checkout (incentivized sign-up).  
- Run a retention pilot on top 5% customers with randomized holdout.

**Quarter 1 (Foundational work — 1–3 months):**
- Build product master and price-history pipeline.  
- Build customer master with normalization rules.  
- Implement ETL dedupe + identity resolution (email normalization, device mapping).

**Quarter 2 (Scale & measurement — 3–6 months):**
- Deploy promotion engine with canonical `promotion_master` table.  
- Implement campaign-exposure logging and automated KPI dashboard.  
- Run controlled campaign experiments and track incremental LTV.

**Owners & roles (suggested):**
- Data Engineering — pipeline, masters, ETL/CDC.  
- Analytics / Data Science — metric definitions, experiment design, dashboards.  
- Marketing Ops — campaign creation, creative, channel execution.  
- CRM / Product — identity-capture UX & integration.

---

## 4. Measurement & KPIs (recommended)
**Core metrics to monitor per campaign and pipeline change:**
- **Retention rate** (30/90/365 days) by segment.  
- **Incremental LTV** (measured via randomized holdouts).  
- **Conversion from anonymous → identified** (% captured at checkout / receipt).  
- **AOV & basket size** by segment & campaign.  
- **Promo ROI** = (incremental revenue − promo cost) / promo cost.  
- **Data quality KPIs**: % missing CustomerID, % duplicate invoices, % inconsistent SKU pricing.

**Targets (example starting points):**
- Identity capture: convert **10–20%** of anonymous buyers within the pilot.  
- Retention pilot (top 2%): aim for **5–10%** lift in repeat purchases over 90 days.  
- Promo coverage: increase recorded discounted transactions from 55 → **500** unique customers while maintaining positive promo ROI.

---

## 5. Next steps & deliverables
1. Convert this document into campaign briefs (one brief per Table A row) with audience SQL, creative specs, and timing.  
2. Implement quick wins in the ingestion pipeline (discount flag, cancellation standardization).  
3. Stand up dashboards: (a) campaign performance, (b) data quality, (c) cohort revenue waterfall.  
4. Begin identity-capture pilot and the top-2% retention holdout experiment.

---
<!-- End of Recommendation.md -->

