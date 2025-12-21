# Data Dictionary - Online Retail (Excel Dashboard)

## 1) Raw Dataset Columns (UCI Online Retail)

| Column | Type | Description |
|---|---|---|
| InvoiceNo | Text | Invoice number. If it starts with “C”, it indicates a cancellation. |
| StockCode | Text | Product/item code. |
| Description | Text | Product/item description (raw). |
| Quantity | Number | Quantity of each item per transaction line. Negative values indicate returns. |
| InvoiceDate | DateTime | Date and time when the transaction was generated. |
| UnitPrice | Number | Unit price in sterling. |
| CustomerID | Text | Customer identifier (may be blank for some transactions). |
| Country | Text | Country where the customer resides. |

## 2) Cleaning Columns (created during cleaning)

| Column | Type | Description |
|---|---|---|
| Description_clean | Text | Cleaned Description (trimmed/cleaned text; blanks filled as “Unknown”; symbols removed via Replace). |
| Price_status | Text | “Valid price” if UnitPrice > 0, else “Invalid price”. |
| quantity_status | Text | “Sale” if Quantity > 0; “Return” if Quantity < 0; “Zero quantity” if Quantity = 0. |
| Invoice_status | Text | “Cancelled” if InvoiceNo starts with C/c; else “Not Cancelled”. |
| Customer_type | Text | “Registered” if CustomerID exists; else “Guest”. |
| Analysis_Include | Text | “Include” if Not Cancelled + Sale + Valid price, else “Exclude”. Used to create clean fact table. |

## 3) Feature Engineering Columns (date/time)

| Column | Type | Description |
|---|---|---|
| Invoice_Date | Date | Date-only version of InvoiceDate (time removed). |
| Invoice_Time | Time | Time-only portion of InvoiceDate. |
| Invoice_Year | Number | Year extracted from Invoice_Date. |
| Invoice_Month | Number | Month number extracted from Invoice_Date (1–12). |
| Invoice_MonthName | Text | Month name (short) extracted from Invoice_Date (e.g., Jan). |
| Invoice_YearMonth | Text | Year-month key formatted as YYYY-MM for monthly trend analysis. |
| Invoice_DayName | Text | Day name (short) from Invoice_Date (e.g., Mon). |
| Invoice_Hour | Number | Hour of day (0 - 23) extracted from InvoiceDate. |
| Invoice_HourLabel | Text | 12-hour readable hour label (e.g., 6AM, 12PM). |

## 4) Analysis Tables

| Table | Description |
|---|---|
| tbl_online_retail | Full dataset table (raw + added columns). |
| tbl_clean_sales | Clean analysis-ready sales lines (Analysis_Include = Include). |
| tbl_exceptions | Excluded rows (Analysis_Include = Exclude) preserved for transparency. |
