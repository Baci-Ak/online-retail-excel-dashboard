# Online Retail — Interactive Excel Dashboard



An end-to-end **Data Analyst portfolio project** built in Excel using the UCI Online Retail dataset.  
It demonstrates a professional workflow: **cleaning → feature engineering → pivot analysis → interactive dashboard → documentation**.

---

## Dashboard Preview
![Online Retail Dashboard](outputs/Dashboard.png)

---

## Project Snapshot
- **Dataset:** UCI Online Retail (UK-based online retailer transactions)
- **Raw rows:** 541,909  
- **Clean rows (analysis-ready):** 530,104  
- **Excluded (exceptions preserved):** 11,805  
- **Included:** 97.82%

---

## What’s Inside
### Cleaning (Excel)
- Cleaned and standardized `Description` (removed symbols, line breaks, blanks → `Unknown`)
- Flagged invalid price lines (`UnitPrice <= 0`)
- Flagged returns / non-sales (`Quantity <= 0`)
- Flagged cancellations (InvoiceNo begins with `C`)
- Preserved excluded rows in `tbl_exceptions` (no silent deletion)

### Feature Engineering (Excel)
- Built date/time fields for slicing and trend analysis (YearMonth, DayName, HourLabel, etc.)
- Built revenue at the line level (`LineRevenue = Quantity * UnitPrice`)

### Dashboard (Excel)
- KPI cards: **Net Sales, Orders, Customers (Registered), AOV**
- Interactive slicers (e.g., Year/Month/Country/Hour)
- Trend + ranking views (Top Countries, Top Products, Hour-of-day sales)
- Dynamic Insights & Recommendations panel

---

## Documentation
- Data dictionary: [`docs/data_dictionary.md`](docs/data_dictionary.md)
- Cleaning rules and assumptions: [`docs/cleaning_log.md`](docs/cleaning_log.md)
- Docs hub: [`docs/README.md`](docs/README.md)

---

## Data Source
- UCI Online Retail dataset: https://archive.ics.uci.edu/dataset/352/online+retail

---

## How to Reproduce
1. Open the workbook: `data/online_retail_workbook.xlsx`
2. Key tables:
   - `tbl_online_retail` (raw + added columns)
   - `tbl_clean_sales` (analysis-ready sales lines)
   - `tbl_exceptions` (excluded rows preserved)
3. Go to the `dashboard` tab and use slicers to explore.

