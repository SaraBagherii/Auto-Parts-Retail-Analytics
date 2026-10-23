# Auto-parts retail analytics | Independent case study

**Role:** Independent analyst (alongside full-time work)  
**Tools:** Excel, Python / pandas  
**Sector:** Automotive parts retail, Romania (client anonymized)

I worked with operational product-line spreadsheets to separate paid transactions from quotes and supplier returns, investigate incomplete customer/order identifiers, and identify customer and product-attachment patterns worth testing. The business question was not simply how much was sold, but which figures were reliable enough to support a decision.

## Read the detailed case study

- [English report (PDF)](reports/Auto_Parts_Retail_Analytics_Case_Study_EN.pdf)
- [گزارش فارسی (PDF)](reports/Auto_Parts_Retail_Analytics_Case_Study_FA.pdf) — right-to-left Persian edition

## Selected findings (observational, not causal)

| Measure | Finding | Interpretation |
| --- | ---: | --- |
| Product-line records reviewed | 13,066 | Operational records, not 13,066 independent orders |
| Identifiable paying customers | 607 | Partial coverage; not all store customers |
| Top 121 identifiable customers' share | 59.2% | Of *identifiable* customer spend only |
| Oil orders with an oil filter | 530 / 752 (70.5%) | Keyword-based product matching, inferred order boundaries |
| Brake-pad orders with brake discs | 43 / 311 (13.8%) | A reason to test a technical inspection prompt, not evidence of lost sales |
| Unresolved line statuses | 2,909 | Excluded from confirmed-paid measures |

**Important data constraints:** 4,843 of 6,940 paid lines lacked an identifiable customer ID; 12,423 dates were carried forward using a documented worksheet rule. Inferred order boundaries, dates, and keyword-based product categories require source validation. The source does not support claims about realized revenue lift, implemented recommendations, audited profit, or year-on-year growth.

## What I did

1. Reviewed source worksheet structures and standardized product-line fields.
2. Parsed quantity-price expressions such as `2X45` into quantity 2, unit price 45, and line amount 90 LEI.
3. Treated `ACHITAT` as paid, `OFERTA` as quoted, and `RETUR` as supplier return; kept ambiguous status records separate.
4. Documented which dates/statuses were explicit and which were inferred; preserved source-row traceability in the working analysis.
5. Analyzed the identifiable customer subset and product co-occurrence within reconstructed paid orders.
6. Proposed small, measurable tests rather than claiming unverified commercial outcomes.

## Repository contents

```text
reports/          Detailed English and Persian case studies
src/              Small, self-contained demonstration of selected cleaning rules
 tests/            Unit tests for the demonstration rules
 docs/             Data definitions, privacy and limitations
 data/             No client data; intentionally empty
```

The **demo code is illustrative** and is **not represented as the original client pipeline**. It uses made-up rows to explain the rules; it cannot reproduce the report's full numerical findings without the confidential source data.

## Run the demonstration

```bash
python -m unittest discover -s tests -v
python src/demo_rules.py
```

No external dependencies are required for the small demonstration. The original analysis used Excel and Python/pandas.

## Confidentiality and outcomes

No client spreadsheets, customer identifiers, contact information, transaction-level exports, or internal commercial files are published here. This repository does not claim the retailer implemented the proposed actions or achieved a sales uplift. It is a demonstration of my analytical approach and professional judgment.

**Relevant collaboration:** sales/customer analytics, operational data cleaning, KPI definitions, reporting QA, and analytics requirements for ERP/CRM teams.
