# Project: Retail Orders — Data Cleaning and Analysis

## Project summary

This effort aimed to clean, validate, and analyze raw retail order records consolidated from multiple internal systems. The source data exhibited inconsistent text formatting, missing fields, duplicate entries, invalid discount values, date-related errors, and discrepancies in sales and profit figures. The goal was to produce a reliable, analysis-ready dataset and generate summary reports for business review.

---

## Repository layout

```bash
part1_data_cleaning/
├── data/
│   ├── raw_orders.xlsx
│   └── cleaned_orders.xlsx
├── outputs/
│   ├── data_quality_report.xlsx
│   ├── pivot_summary.xlsx
│   └── cleaning_log.md
├── screenshots/
│   ├── raw_data_preview.png
│   ├── cleaned_data_preview.png
│   ├── pivot_summary_1.png
│   └── pivot_summary_2.png
└── README.md
```

---

## File descriptions

**raw_orders.xlsx:** Original exported dataset, left unchanged.

**cleaned_orders.xlsx:** Processed dataset with standardized text, validated dates, derived columns, and quality flags.

**data_quality_report.xlsx:** Summaries of missing values, duplicates, invalid discounts, date problems, order-status issues, sales/profit discrepancies, and counts of clean vs flagged records.

**pivot_summary.xlsx:** Business-oriented pivot reports such as:

* Sales and profit by region
* Sales and profit by category and sub-category
* Order counts by ship mode
* Profit margin by customer segment
* Refunded/cancelled/failed orders by region
* Monthly sales trend

**cleaning_log.md:** Record of cleaning steps, applied business rules, assumptions, flagged records, and project limitations.

---

## Work completed

### Preserve raw data

Kept the original file intact; all cleaning was applied to a separate output file.

### Standardize text fields

Cleaned and normalized: customer_name, segment, region, state, city, category, sub_category, ship_mode, payment_status, order_status.

Actions included trimming extra spaces, removing leading/trailing whitespace, normalizing case, and substituting “Unknown” where appropriate.

### Validate and fix dates

Validated order_date and ship_date.

Checked for missing or invalid dates and for ship dates preceding order dates.

Added shipping_delay_days.

### Identify duplicates

Detected exact duplicate rows and order IDs with conflicting information.

Flagged duplicates and summarized them in the data quality report.

### Enforce business rules

Applied rules for missing region and ship mode, missing or invalid discounts, cancelled/failed/refunded orders, and invalid shipping records.

### Add derived columns

Created cleaned_discount, calculated_sales, calculated_profit, profit_margin, shipping_delay_days, order_month, order_year, and data_quality_flag.

### Produce data quality report

Generated detailed summaries: missing values, duplicates, invalid discounts, date issues, order-status problems, sales/profit mismatches, and final clean vs flagged counts.

### Create pivot summary

Built pivot tables and summaries intended for business analysis and decision-making.

### Maintain cleaning log

Documented all cleaning steps, assumptions, business logic, flagged records, and known limitations.

---

## Final result

The raw data was successfully cleaned, validated, and converted into an analysis-ready dataset. Supporting reports and pivot summaries were produced to inform business reviews and decision-making.
