# Data Dictionary

The source workbook contains 9,994 transaction-line records and 21 columns. Each row represents a line item within an order.

| Column | Meaning |
|---|---|
| Row ID | Source row identifier |
| Order ID | Order identifier; may repeat across multiple line items |
| Order Date | Date the order was placed |
| Ship Date | Date the order was shipped |
| Ship Mode | Shipping method |
| Customer ID | Customer identifier |
| Customer Name | Customer name in the source data |
| Segment | Customer segment |
| Country/Region | Country or region field as supplied by the source |
| City | City |
| State | State or province |
| Postal Code | Postal code; missing source values are represented as `Unknown` in the cleaned output |
| Region | Sales region |
| Product ID | Product identifier |
| Category | Product category |
| Sub-Category | Product sub-category |
| Product Name | Product name |
| Sales | Sales amount for the transaction line |
| Quantity | Units in the transaction line |
| Discount | Discount fraction recorded for the transaction line |
| Profit | Profit amount for the transaction line |

## Derived fields in the cleaned output

- `Profit Margin`: line-level profit divided by line-level sales.
- `Shipping Duration`: difference between ship date and order date in days.
- `Sales Performance Category`: Low / Medium / High band based on the first and third sales quartiles.
- `is_sales_outlier`: flag for sales values outside the 1.5×IQR bounds; outliers are flagged, not automatically deleted.
- `Year` and `Month`: order-date components used for trend analysis.
