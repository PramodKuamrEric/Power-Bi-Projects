## Orders Table – Data Cleaning

The `Orders` table was reviewed and cleaned before using it for Power BI data modeling and dashboard development.

### 1. Discount Formatting

The `Discount` column was formatted as a **Percentage** so that discount values could be correctly interpreted and displayed in the dashboard.

**Action taken:**

* Changed the `Discount` column format to **Percentage**.

**Result:**
Discount values are now displayed consistently as percentages.

---

### 2. Payment Method Standardization

The `Payment Method` column contained inconsistent formatting for the same payment method.

**Issue identified:**

* `upi`
* `UPI`

**Actions taken:**

* Replaced `upi` with `UPI`.
* Applied **Trim** to remove unnecessary leading and trailing spaces.

**Result:**
`UPI` is now treated as a single standardized payment method instead of appearing as duplicate categories.

---

### 3. Order Status Standardization

The `Order Status` column contained inconsistent capitalization.

**Issue identified:**

* `delivered`
* `Delivered`

**Action taken:**

* Replaced `delivered` with `Delivered`.

**Result:**
The `Delivered` status is now standardized and does not appear as a separate duplicate category in Power BI filters or slicers.

---

### 4. Data Validation

After completing the cleaning process, the affected columns were reviewed to verify consistency.

**Validation performed:**

* Checked `Discount` formatting.
* Checked `Payment Method` for inconsistent values and whitespace.
* Checked `Order Status` for inconsistent capitalization.
* Verified the cleaned categories in Power BI.

### Final Outcome

The `Orders` table was standardized and prepared for Power BI data modeling, calculations, filters, slicers, and dashboard visualizations.
