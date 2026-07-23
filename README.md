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

![Dashboard Screenshot](docs/dashboard_screenshots/Clean%20Dashboard.png)

*Built in Databricks SQL Dashboards, with global filters on `category_name` and `transaction_date` applied across all visuals.*

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
