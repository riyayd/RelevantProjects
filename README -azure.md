# Azure Market Data Pipeline

An end-to-end Python ETL pipeline for fetching, validating, and storing financial market data using **Azure Blob Storage** — mirroring real workflows in asset management and investment data teams.

## What it does

1. **Fetches live market data** for equities and indices (Munich Re, Allianz, Deutsche Bank, S&P 500) via yfinance
2. **Runs data quality checks** — missing values, negative prices, extreme returns (>20%), duplicates, zero volume
3. **Uploads processed data and quality reports** to Azure Blob Storage
4. **Retrieves data back from Azure** and runs analysis
5. **Visualises** price trends, return distributions, and anomaly flags in a dashboard

## Tech stack

- Python · pandas · NumPy
- Azure Blob Storage (`azure-storage-blob`)
- yfinance (market data)
- Matplotlib · Seaborn

## How to run

```bash
# 1. Install dependencies
pip install yfinance azure-storage-blob pandas matplotlib seaborn jupyter

# 2. Set your Azure connection string
export AZURE_STORAGE_CONNECTION_STRING="your_connection_string_here"
# Get this from: Azure Portal → Storage Account → Access keys

# 3. Launch notebook
jupyter notebook Azure_Market_Data_Pipeline.ipynb
```

Or run directly in **Google Colab** — upload the notebook and paste your connection string in Step 2.

## Pipeline output

| Output | Location |
|--------|----------|
| Processed market data | Azure Blob: `processed/market_data_YYYYMMDD.csv` |
| Data quality report | Azure Blob: `reports/quality_report_YYYYMMDD.csv` |
| Analysis dashboard | Local: `market_data_dashboard.png` |

## Data quality checks

| Check | Action |
|-------|--------|
| Missing values | Forward-fill, drop remaining |
| Negative/zero prices | Remove rows |
| Extreme daily returns (>20%) | Flag as anomaly |
| Duplicate date/ticker rows | Keep first occurrence |
| Zero volume days | Flag as likely market holiday |

## Related projects

- [`ML_Bias_Audit_Tool.ipynb`](../ML_Bias_Audit_Tool/ML_Bias_Audit_Tool.ipynb) — ML pipeline on Databricks
- [`NetflixStockForcasting.ipynb`](../NetflixStockForcasting.ipynb) — ARIMA time series forecasting
- [`Risk_Management_101.ipynb`](../Risk_Management_101.ipynb) — financial risk analysis

---

*MSc Computational & Applied Mathematics, FAU Erlangen-Nürnberg*
