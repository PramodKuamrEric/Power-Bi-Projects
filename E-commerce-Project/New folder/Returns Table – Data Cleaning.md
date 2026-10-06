## Returns Table – Data Cleaning

The `Returns` table was checked and cleaned to remove incomplete records before using the data in the Power BI dashboard.

### 1. Missing Values Check

The `Returns` table contained 2 rows with missing (`null`) values.

**Issue identified:**

* 2 records contained `null` values.
* These records did not have complete information needed for analysis.

**Action taken:**

* Applied a filter in Power Query to exclude the rows containing `null` values.
* The original source data was not deleted.

**Result:**

The 2 incomplete records were removed from the Power BI analysis, while the original source data remained unchanged.

---

### 2. Return Status Check

The `Return Status` column contained valid return statuses.

**Values identified:**

* `damaged`
* `refunded`

**Action taken:**

* Checked the values to make sure they represented valid return information.
* Kept both `damaged` and `refunded` values because they are useful for return analysis.

**Result:**

Valid return statuses were kept and are available for Power BI filters, slicers, and visualizations.

---

### 3. Data Validation

After cleaning, the `Returns` table was checked again.

**Validation performed:**

* Checked for remaining `null` values.
* Verified that valid return statuses were still available.
* Checked that the filtering step was applied correctly in Power Query.

### Final Outcome

The `Returns` table was cleaned by excluding 2 incomplete records while keeping valid return information. The table is now ready for Power BI data modeling, return analysis, filters, slicers, and dashboard visualizations.