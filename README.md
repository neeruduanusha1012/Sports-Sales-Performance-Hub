<img width="1167" height="775" alt=""Sports sales dashboard"" src="https://github.com/user-attachments/assets/415c63cd-745a-450c-ac18-66a42a847003" />
#Sports Sales Data Pipeline on Databricks
End-to-end pipeline for an FMCG sports brand: raw CSV files to a BI dashboard.

## How to run
1. `setup_catalog.ipynb`: creates the catalog, schemas and volumes
2.Raw CSV -> Bronze (raw + audit metadata) -> Silver (cleaned, deduplicated) -> Gold (star schema)
3. Facts: `1_full_load_fact` → `2_incremental_load_fact`

**Gold layer (star schema)**
- Fact: `fact_orders`
- Dimensions: `dim_customers`, `dim_products`, `dim_gross_price`, `dim_date`

## Architecture
Raw CSV -> Bronze (raw + audit metadata) -> Silver (cleaned, deduplicated) -> Gold (star schema)

## Highlights
- 4 sources: customers, products, pricing, daily orders
- Fixes: duplicates, 4+ date formats, negative prices, null quantities
- Incremental loads with file archival (no duplicates on re-run)
- Delta Change Data Feed enabled
- Moved raw data from S3 to Unity Catalog Volumes after a 403 on serverless

## Dashboard
sports sales built on Databricks AI/BI (screenshots in /dashboard)

## Tech stack
PySpark, Delta Lake, Unity Catalog, Databricks Serverless, SQL

## Author
Anusha Neerudu | [linkedin.com/in/neerudu-anusha#](https://www.linkedin.com/in/neerudu-anusha/) Sports-Sales-Performance-Hub
sports-sales-databricks-lakehouse
