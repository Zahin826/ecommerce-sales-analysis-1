# E-commerce Sales Analysis

Cleaning and analyzing messy online retail sales data with Python (pandas and matplotlib).

## Goal

Take a raw, messy e-commerce dataset, clean it step by step, and answer business questions: which countries earn the most, and which months sell best.

## Dataset

Online Retail II (UCI Machine Learning Repository, also on Kaggle). It holds real transactions from a UK-based online shop between 2009 and 2011.

- 1,067,371 rows and 8 columns before cleaning
- Columns: Invoice, StockCode, Description, Quantity, InvoiceDate, Price, Customer ID, Country
- The data file is not included in this repo because of its size. Download it from Kaggle and place it in a folder named `data/`.

## Cleaning steps

| Step | What I did | Rows after |
|------|-----------|-----------|
| 1 | Removed 34,335 exact duplicate rows | 1,033,036 |
| 2 | Converted InvoiceDate from text to real dates | 1,033,036 |
| 3 | Moved cancelled orders (invoices starting with "C") into a separate table, 19,104 rows | 1,013,932 |
| 4 | Removed rows with a price of zero or less, 6,019 rows | 1,007,913 |
| 5 | Added a Revenue column (Quantity x Price) | 1,007,913 |

Decision on missing values: about 243,000 rows (roughly 23%) had no Customer ID. I kept them, because they are real sales and still valid for country, product and month analysis. They are not usable for customer-level questions.

## Key findings

1. **The business is overwhelmingly UK-based.** The UK earned about 17.4M GBP, around 26 times more than the next country, Ireland (EIRE).
2. **Top international markets:** EIRE (about 0.66M GBP), Netherlands (0.55M), Germany (0.43M) and France (0.35M).
3. **Sales are seasonal.** Revenue climbs from September and peaks in November at about 2.97M GBP. February is the weakest month at about 1.07M GBP.

Note: monthly totals combine all years in the data, so they show a general pattern and not exact yearly figures.

## Charts

![Revenue by month](images/revenue_by_month.png)
![Revenue by country](images/revenue_by_country.png)
![Top international countries](images/top_international_countries.png)

## Project structure

```
ecommerce-sales-analysis-1/
  data/          raw and cleaned data (not uploaded)
  images/        charts used in this README
  notebooks/
    01_cleaning.ipynb    data cleaning
    02_analysis.ipynb    analysis and charts
  README.md
```

## How to run

1. Download Online Retail II from Kaggle and save it as `data/online_retail_II.csv`.
2. Install the tools: `pip install pandas matplotlib openpyxl jupyter ipykernel`
3. Run `01_cleaning.ipynb` first, then `02_analysis.ipynb`.

## Tools used

Python, pandas, matplotlib, Jupyter Notebook, Git and GitHub.

## Next steps

- Top products by revenue
- Customer counts and repeat buyers
- Returns analysis

## Author

Zahin ([GitHub](https://github.com/Zahin826))