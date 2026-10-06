## Data Cleaning – Before & After Summary

The following summary shows the main data quality issues identified in the raw dataset and the cleaning actions performed before using the data for Power BI analysis.

| Table | Column | Before Cleaning | Cleaning Action | After Cleaning |
|---|---|---|---|---|
| Customer | City | `mumbai`, `Mumbai` | Replaced `mumbai` with `Mumbai` | `Mumbai` |
| Customer | Customer Segment | One blank value | Replaced blank with `New` | No blank values |
| Customer | State | `rajasthan`, `Rajasthan` | Standardized capitalization | `Rajasthan` |
| Customer | State | Duplicate-looking values caused by extra spaces | Applied **Trim** | Standardized state values |
| Orders | Discount | Numeric discount values | Changed format to Percentage | Percentage format |
| Orders | Payment Method | `upi`, `UPI` and possible extra spaces | Standardized to `UPI` + applied **Trim** | `UPI` |
| Orders | Order Status | `delivered`, `Delivered` | Replaced `delivered` with `Delivered` | `Delivered` |
| Products | Category | `Electronic`, `Electronic ` | Applied **Trim** | Single standardized value |
| Products | Sub-Category | `audio`, `Audio` | Replaced `audio` with `Audio` | `Audio` |
| Returns | Return Records | 2 records contained `null` values | Filtered out incomplete rows in Power Query | Incomplete rows excluded |
| Returns | Return Status | `damaged`, `refunded` | Checked and retained valid values | `damaged`, `refunded` |

### Overall Data Quality Improvements

* Standardized inconsistent capitalization across categorical columns.
* Removed unnecessary leading and trailing spaces using **Trim**.
* Handled the missing `Customer Segment` value.
* Standardized discount formatting as a percentage.
* Standardized payment methods and order statuses.
* Standardized product categories and sub-categories.
* Excluded 2 incomplete records from the `Returns` table using a Power Query filter.
* Retained valid return statuses such as `damaged` and `refunded`.
* Improved consistency for Power BI filters, slicers, calculations, and visualizations.

### Final Outcome

After cleaning, the dataset was standardized and prepared for **data modeling, DAX calculations, and Power BI dashboard development**.

The original source data was not permanently modified; cleaning and filtering were performed in **Power Query**.