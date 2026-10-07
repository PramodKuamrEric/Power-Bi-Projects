## Data Cleaning & Standardization

Before building the Power BI dashboard, I reviewed the customer dataset and performed data cleaning to improve consistency, accuracy, and usability.

### 1. City Name Standardization

I found inconsistent capitalization in the `City` column.

**Issue identified:**

* `mumbai`
* `Mumbai`

Both values represented the same city but were treated as different values.

**Action taken:**

* Replaced `mumbai` with the standardized value `Mumbai`.

**Result:**
City names now follow a consistent capitalization format, preventing duplicate-looking values in Power BI filters and slicers.

---

### 2. Customer Segment – Missing Value

The `Customer Segment` column contained three existing categories:

* `New`
* `Regular`
* `Prime`

During the data review, I found **one blank cell** in this column.

**Action taken:**

* Replaced the single blank value with `New`.

**Reason:**
The dataset contained only one missing value in this field, and the record was categorized as a `New` customer to maintain a complete customer-segment classification.

**Result:**
There are no blank values remaining in the `Customer Segment` column.

---

### 3. State Name Standardization

The `State` column contained inconsistent values caused by capitalization and formatting differences.

**Issues identified:**

* `rajasthan` and `Rajasthan`
* Inconsistent formatting in `Karnataka`

**Actions taken:**

* Replaced `rajasthan` with `Rajasthan`.
* Applied **Trim** to remove unnecessary leading and trailing spaces.
* Standardized the state values.

**Result:**
Each state is represented consistently, preventing duplicate-looking state values in Power BI filters and slicers.

---

### 4. Data Validation

After completing the cleaning process, I reviewed the affected columns again to verify the results.

**Validation performed:**

* Checked city names for inconsistent capitalization.
* Checked `Customer Segment` for blank values.
* Checked state names for duplicate-looking values caused by formatting.
* Verified the cleaned values in Power BI filters/slicers.

### Final Outcome

The customer dataset was standardized and prepared for further analysis and Power BI dashboard development.
