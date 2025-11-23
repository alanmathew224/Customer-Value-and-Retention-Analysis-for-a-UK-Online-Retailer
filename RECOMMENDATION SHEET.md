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

| Segment | Status | Objective | Tactic | Channel | Offer example | KPI | Priority |
|---|---:|---|---|---|---|---:|---:|
| VIP / Elite | Active | Increase repeat frequency & AOV | Personalized high-value bundles + early access | Email + Account Manager | 10% off Top SKUs + VIP-only bundle | Incremental LTV, repeat rate | High |
| VIP / Elite | At-risk (declining) | Prevent churn | Retention outreach + 1:1 promo + service recovery | Phone / Email | £20 credit + dedicated rep | Churn rate, retention lift | High |
| Premium | Active | Grow spend tier | Targeted cross-sell using Top SKUs | Email, SMS | Product-bundle discount (single-use) | AOV, basket size | High |
| Mass | Active | Improve conversion & margin | Category promotions + product recommendations | Email, onsite banners | 15% off selected Mid products | Conversion rate, margin impact | Medium |
| Hibernating | Dormant / Lost | Re-activation | Re-engagement promo tied to category preference | Email + Paid Social | 25% off Bottom→Mid product upgrade | Reactivation rate, ARPU | Medium |
| Anonymous | Any | Capture identity & enable targeting | Incentivized identity capture at checkout | Checkout modal, email-on-receipt | 10% off next order for sign-up | % converted to identified, LTV | High |

> _Add your campaign rows to this table. Replace examples with completed offers from `Recommendation.md` or marketing stakeholders._


### Table B — Campaign playbook: behavior-based offers
Columns: **Behavior | Objective | Offer type / messaging | Timing | KPI**

| Behavior | Objective | Offer type / messaging | Timing | KPI |
|---|---|---|---:|---:|
| Unknown frequency (<5 purchases) | Drive repeat and higher-margin purchases | Mid-tier upsell with trial bundle; emphasize quality & value | 2–4 weeks after purchase | Repeat rate in 90 days, AOV |
| Wholesaler / High-frequency | Improve retention and margin | Volume pricing, subscription or account-level discounts; negotiable terms | Ongoing (account mgmt) | Retention rate, GM% |
| Seasonal (fall spike) | Capture peak revenue + smooth off-season | Time-limited bundles and early-bird offers for next season | Pre-fall & Fall peak | Incremental seasonal revenue |
| New customer (Top-product promo) | Convert to repeat at higher AOV | “Welcome bundle” with Top products + small cross-sell | First 30 days | 30/90-day repeat, AOV |
| Hibernating | Re-activation & test upgrade | Deep discount on Mid product + cross-sell into Top | Re-activation campaign window | Reactivation rate, CLTV uplift |

> _Use this playbook as campaign templates. Each row should be converted into a campaign brief (audience definition, creative, timing, KPI, and experiment design)._

---

## 2. Data & Analytics Pipeline Improvements — Requirements & Rationale
**Goal:** make targeting, attribution, experiment measurement, and personalization reliable and reproducible.

### Required changes (short, business‑facing descriptions)
- **Add `discount_flag` to transactions.** Rationale: enable tracking of discount behaviour, promo attribution, and discount-driven margin analysis.
- **Standardise cancel/return invoice linkage.** All cancellation invoices must reuse the original invoice number prefixed with `C` (e.g., `12345` → `C12345`). Rationale: deterministic join between sale and return for accurate net revenue and churn analysis.
- **Create canonical `product` master.** Columns: `product_id` (StockCode), `name`, `product_category` (tier: Top/Mid/Bottom), `specs`, `date_added`, `current_price`, `price_before`, `price_change_date`. Rationale: avoid duplicate SKUs, support price-history analyses, and enable product-level propensity models.
- **Create canonical `customer` master.** Columns: `customer_id`, `email` (normalized), `name`, `country`, `date_joined`, `lifecycle_status`, `segment`, `source_channel`. Rationale: unified identity for segmentation, personalization, and LTV modeling.
- **Enforce one-to-one mapping for `StockCode` → `Description` & `UnitPrice`.** Rationale: prevents double-counting and inconsistent product aggregates.
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
- Retention pilot (top 5%): aim for **5–10%** lift in repeat purchases over 90 days.  
- Promo coverage: increase recorded discounted transactions from 55 → **500** unique customers while maintaining positive promo ROI.

---

## 5. Next steps & deliverables
1. Convert this document into campaign briefs (one brief per Table A row) with audience SQL, creative specs, and timing.  
2. Implement quick wins in the ingestion pipeline (discount flag, cancellation standardization).  
3. Stand up dashboards: (a) campaign performance, (b) data quality, (c) cohort revenue waterfall.  
4. Begin identity-capture pilot and the top-5% retention holdout experiment.

---
<!-- End of Recommendation.md -->

