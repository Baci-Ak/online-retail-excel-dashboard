# Documentation Hub - Online Retail Excel Dashboard

This folder contains the detailed documentation supporting the project.

## Contents
- **Data dictionary:** [data dictionary](docs\data_dictionary.md)  
  Definitions for raw columns, cleaning/status fields, and engineered date/time features.

- **Cleaning log:** [Data cleaning log](docs\cleaning_log.md)  
  Cleaning rules, decisions, assumptions, and cleaning summary counts.

## Workbook References
Key tables inside the Excel workbook:
- `tbl_online_retail` - raw data + added columns
- `tbl_clean_sales` - analysis-ready sales lines (Include)
- `tbl_exceptions` - excluded rows (exceptions preserved)

## Next Phase
The next phase of the project adds:
- PivotTables for KPIs and trends
- An interactive Excel dashboard
- Exports into `outputs/` (PDF/screenshots) and updated documentation
