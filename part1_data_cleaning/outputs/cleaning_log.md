# Retail Orders — Data Cleaning & Validation

## Issues Detected

* Missing values for region, ship mode, and discount.
* Duplicate records present.
* Duplicate order IDs with inconsistent details.
* Invalid discount entries (negative or exceeding allowed limits).
* Missing or malformed dates.
* Ship dates that occur before order dates.
* Mismatches in sales and profit calculations.
* Inconsistent order statuses.
* Inconsistent payment statuses.

---

## Cleaning Steps Performed

### Text Normalization

* Standardized and cleaned these fields: `customer_name`, `segment`, `region`, `state`, `city`, `category`, `sub_category`, `ship_mode`, `payment_status`, `order_status`.
* Removed extra and leading/trailing whitespace.
* Harmonized text casing.
* Replaced certain missing values with “Unknown” where appropriate.

### Date Validation

* Verified `order_date` and `ship_date`.
* Checked for missing or invalid dates.
* Flagged ship dates earlier than order dates.
* Created a derived field `shipping_delay_days`.

### Duplicate Management

* Located exact duplicate rows and order IDs with conflicting records.
* Exact duplicates were detected with duplicate-detection logic.
* Order ID conflicts were marked for manual review rather than auto-resolved.

---

## Business Rules Applied

* Missing region: filled with “Unknown” and recorded in the quality report.
* Missing ship mode: filled with “Unknown” and recorded in the quality report.
* Missing discount: treated as 0 only when other sales-related fields were valid.
* Negative discounts: flagged as invalid.
* Discounts exceeding allowed range: flagged as invalid.
* Cancelled orders: excluded from the completed-sales summary.
* Failed payments: excluded from the completed-sales summary.
* Refunded orders: reported separately.
* Ship dates earlier than order dates: flagged as invalid shipping records.

---

## Assumptions and Handling Choices

* Missing discounts were assumed to be 0 if accompanying sales fields looked valid.
* Missing region and ship mode values were replaced with “Unknown.”
* Conflicting duplicate order IDs were not removed automatically; they were left for business review.
* Invalid records were kept in the dataset for reporting and audit purposes.

---

## Records Removed and Flagged

* Exact duplicate rows removed: **0**
* Records flagged for review included: duplicate conflicts, invalid discounts, date problems, shipping issues, and sales/profit mismatches.

---

## Limitations

* Several flagged items require manual business review to resolve.
* Conflicting duplicate records were not automatically reconciled.
* Aggregations and pivot summaries rely on the quality of the cleaned dataset.
* Some business-validation choices were necessarily based on assumptions because the raw data were incomplete.

---

## Final Outcome

The dataset was cleaned and transformed into an analysis-ready version for business reporting and further review.
