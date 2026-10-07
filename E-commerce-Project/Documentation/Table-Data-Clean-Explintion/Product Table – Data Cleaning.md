## Product Table – Data Cleaning

The `Products` table was reviewed and cleaned to standardize category and sub-category values before building the Power BI dashboard.

### 1. Category Standardization

The `Category` column contained duplicate-looking values caused by unnecessary whitespace.

**Issue identified:**

* `Electronic`
* `Electronic `

Both values represented the same category.

**Action taken:**

* Applied **Trim** to the `Category` column to remove unnecessary leading and trailing spaces.

**Result:**
The duplicate-looking `Electronic` values were standardized into a single category.

---

### 2. Sub-Category Standardization

The `Sub-Category` column contained inconsistent capitalization.

**Issue identified:**

* `audio`
* `Audio`

Both values represented the same sub-category.

**Action taken:**

* Replaced `audio` with the standardized value `Audio`.

**Result:**
The `Audio` sub-category is now represented consistently and does not appear as a separate duplicate category in Power BI filters and slicers.

---

### 3. Data Validation

After cleaning, the affected columns were reviewed again.

**Validation performed:**

* Checked `Category` for unnecessary spaces.
* Checked `Sub-Category` for inconsistent capitalization.
* Verified that duplicate-looking category values were removed from Power BI filters and slicers.

### Final Outcome

The `Products` table was standardized and prepared for Power BI data modeling, product-level analysis, filters, slicers, and dashboard visualizations.
