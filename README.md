# Ecommerce Medallion Data Pipeline (Databricks)

End-to-end e-commerce data engineering project built on Databricks, using the **Medallion Architecture** (Bronze → Silver → Gold) to ingest, clean, model, and analyze 3 months of e-commerce transaction data — covering orders, customers, products, brands, and calendar/date dimensions — with a fully interactive SQL dashboard on top.

---

## 📌 Project Overview

Raw e-commerce data (orders, customers, products, brands, dates) is ingested and progressively refined through three layers:

- **Bronze** – Raw data ingestion, minimal transformation, source-of-truth snapshot
- **Silver** – Cleaned, validated, deduplicated, and conformed data (fact + dimension staging)
- **Gold** – Final star-schema model (fact + dimension tables) ready for analytics and BI consumption

The Gold layer feeds a SQL dashboard built directly in Databricks for business-facing insights.

---

## 🏗️ Architecture

```
Raw Source Data
      │
      ▼
 ┌──────────┐      ┌──────────┐      ┌──────────┐
 │  BRONZE  │ ───▶ │  SILVER  │ ───▶ │   GOLD   │ ───▶  Dashboard
 │  (raw)   │      │ (clean)  │      │ (star     │
 │          │      │          │      │  schema)  │
 └──────────┘      └──────────┘      └──────────┘
```

**Star Schema (Gold Layer):**

```
                dim_date
                    │
dim_customer ── fact_transactions_denorm ── dim_product
                    │
                dim_brand
```

Fact table: `fact_transactions_denorm`
Dimension tables: `dim_date`, `dim_customer`, `dim_product`, `dim_brand`

---

## 📂 Repository Structure

```
ecommerce-medallion-pipeline/
├── Bronze/                  # Raw data ingestion notebooks
├── Silver/                  # Cleaning, deduplication, conformance
│   ├── 1DimSilver.ipynb
│   └── 1FactSilver.ipynb
├── Gold/                    # Final fact/dimension star schema
│   ├── 1DimGold.ipynb
│   └── 1FactBronze.ipynb
├── Catalogue Setup/          # Unity Catalog / schema setup scripts
│   └── catalogueSetup.ipynb
├── Analysis part/             # Dashboard queries & analysis notebooks
├── docs/
│   └── dashboard_screenshots/  # Dashboard preview images
└── README.md
```

---

## 🛠️ Tech Stack

- **Platform:** Databricks (Free Edition)
- **Processing:** PySpark, Spark SQL
- **Storage:** Delta Lake
- **Catalog:** Unity Catalog (`ecommerce.bronze`, `ecommerce.silver`, `ecommerce.gold`)
- **BI/Visualization:** Databricks SQL Dashboard

---

## 📊 Dashboard: Ecommerce Analysis

Built directly in Databricks SQL, the dashboard is interactive with global filters on `category_name` and `transaction_date`, and includes:

| Visual | Description |
|---|---|
| **Top Selling Categories by Revenue** | Bar chart ranking categories by summed net amount |
| **Revenue Trend by Month** | Line chart tracking revenue across the 3-month period |
| **Revenue Heatmap by Day & Hour** | Heatmap showing peak transaction times by day of week and hour of day |

![Dashboard Screenshot](docs/dashboard_screenshots/ecommerce_analysis_dashboard.png)

*(Add your dashboard screenshots to `docs/dashboard_screenshots/` and update the path above)*

---

## 🔑 Key Data Engineering Concepts Applied

- Medallion architecture (Bronze/Silver/Gold layering)
- Star schema dimensional modeling
- Delta Lake managed tables via Unity Catalog
- Data cleaning: deduplication, null handling, type casting
- Denormalized fact table design (`fact_transactions_denorm`) for query performance
- Date dimension engineering (month name, day name, weekend flag, quarter, week of year)
- SQL-based aggregation and time-based analysis (hour-of-day extraction, monthly trends)

---

## 🚀 How to Run

1. Clone this repo into a Databricks Repos folder
2. Run notebooks in order: `Catalogue Setup` → `Bronze` → `Silver` → `Gold`
3. Open the `Ecommerce Analysis` dashboard (SQL Dashboards section) to view results

---

## 📈 What's Next

- Add dbt for transformation orchestration and testing
- Introduce Airflow for pipeline scheduling
- Extend to streaming ingestion for real-time order data
- Migrate to Azure Databricks with ADLS Gen2 as storage layer

---

## 👤 Author

**Manichandu**
Digital Quality Engineer → transitioning into Data Engineering
[GitHub](https://github.com/Manichandu2210) · [LinkedIn](https://linkedin.com/in/b-manichandu-729836337)
