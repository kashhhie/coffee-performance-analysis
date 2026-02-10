# Coffee Performance Analysis

This repository contains sales data and a dashboard screenshot to help evaluate a coffee shop's performance. The README below explains the dataset, the dashboard contents, and clear, Excel-only steps to reproduce common analyses and charts.

## Quick Dataset Summary

- **File:** raw data/index_coffe (1).xlsx
- **Records:** 1,134 rows
- **Columns:** 6

Columns and meaning:

- `date` — Excel serial date (integer part represents date)
- `datetime` — Excel serial date with fractional day (date + time)
- `cash_type` — Payment method (e.g., `card`, `cash`)
- `card` — Anonymized customer identifier (text)
- `money` — Transaction amount (numeric)
- `coffee_name` — Product name (text)

Note: Dates appear as Excel serial numbers (for example `45352`); format the cells as Date/Time in Excel to view readable dates.

## Dashboard (dashboard/Screenshot 2026-02-09 183922.png)

- The dashboard image shows at-a-glance sales performance (total revenue and trends), top-selling products, and payment method breakdown. Use the Excel steps below to recreate these charts.

## What to analyze (simple goals)

- Total revenue and revenue by product
- Number of transactions and average transaction value
- Top-selling coffee types by count and revenue
- Hourly and daily sales patterns (peak hours)
- Payment method distribution (card vs cash)
- Top customers (by `card` ID) and repeat purchase behavior

## Excel data cleaning

1. Open `raw data/index_coffe (1).xlsx` in Excel.

2. Convert date columns
- Select the `date` or `datetime` column cells.
- Right-click → Format Cells → Date or Custom.
- For both date and time, use Custom: `yyyy-mm-dd hh:mm`.

3. Add helper columns
- `DateOnly`: =INT([@datetime]) → gives the calendar date.
- `Hour`: =HOUR([@datetime]) → extracts the hour for hourly trend.

4. Create a Pivot Table for revenue & counts
- Insert → PivotTable → select the whole table as source.
- To get revenue by product: Drag `coffee_name` to Rows, `money` to Values (set to Sum), and again `money` to Values (set to Count) for volumes.

5. Create time-based charts
- Daily revenue: In PivotTable, put `DateOnly` in Rows and `money` (Sum) in Values. Insert → Line Chart.
- Hourly pattern: Put `Hour` in Rows and `money` (Sum) in Values. Insert → Column Chart.

6. Payment method breakdown
- New Pivot: `cash_type` in Rows and `money` (Count) in Values. Insert → Pie Chart or Column Chart.

7. Top customers
- Pivot with `card` in Rows and `money` in Values (Sum and Count). Sort Sum of `money` descending to find top spenders.

8. Price summary and checks
- Use formulas: `=MIN(money)`, `=MAX(money)`, `=AVERAGE(money)` to get price range and average.

9. Clean & validation
- Ensure `coffee_name` values are consistent (trim spaces, fix typos).
- Check for duplicates and unexpected zero/negative `money` values.
- If times/dates look incorrect, try formatting or convert text-to-columns.

## Next steps (after initial Excel analysis)

- Standardize `coffee_name` values for accurate grouping.
- Build a small dashboard sheet in Excel using PivotCharts and Slicers for interactivity.
- Export cleaned data (CSV) if you plan to use code-based tools later.

## Files

- raw data/index_coffe (1).xlsx — source sales data
- dashboard/Screenshot 2026-02-09 183922.png — example dashboard visualization
