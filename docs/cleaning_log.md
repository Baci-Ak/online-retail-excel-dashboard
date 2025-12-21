# Cleaning Log - Online Retail (Excel Dashboard)

## Goal
Create a reliable analysis-ready sales table for PivotTables and dashboarding, while preserving excluded records for transparency.

## Cleaning Summary
- Total rows (raw): 541,909
- Included rows (clean): 530,104
- Excluded rows (exceptions): 11,805
- % included: 97.82%

## Cleaning Actions Performed

### 1) Description cleaning
Created `Description_clean` and standardised product descriptions:
- Removed non-printing characters and inconsistent spacing (TRIM/CLEAN style logic)
- Removed question marks `?` (escaped wildcard using `~?` in Find & Replace)
- Removed asterisks `*` using Find & Replace
- Replaced line breaks using Find & Replace (Ctrl+J → space)
- Compressed double spaces into single spaces
- Replaced blank descriptions with `Unknown`

### 2) Price cleaning (UnitPrice)
Created `Price_status`:
- Valid price: UnitPrice > 0
- Invalid price: UnitPrice <= 0

### 3) Quantity cleaning
Created `quantity_status`:
- Sale: Quantity > 0
- Return: Quantity < 0
- Zero quantity: Quantity = 0

### 4) Cancellation identification
Created `Invoice_status`:
- Cancelled: InvoiceNo begins with “C” (case-insensitive)
- Not Cancelled: otherwise

### 5) Customer identification
Created `Customer_type`:
- Registered: CustomerID not blank
- Guest: CustomerID blank

## Analysis Inclusion Rule
Created `Analysis_Include`:
- Include rows only when:
  - Invoice_status = Not Cancelled
  - quantity_status = Sale
  - Price_status = Valid price
- All other rows are Exclude

## Output Tables
- `tbl_clean_sales`: Analysis-ready sales lines (Include)
- `tbl_exceptions`: Excluded rows preserved for audit and transparency

## Notes / Assumptions
- Returns and cancellations are real business events and were not deleted; they were excluded from fulfilled-sales analysis and preserved in `tbl_exceptions`.
- Guest customers (blank CustomerID) are retained for revenue analysis but must be handled carefully for customer-count metrics.
