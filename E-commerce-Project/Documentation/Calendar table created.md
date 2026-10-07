## 📅 Calendar Table – Power BI

A dedicated Calendar table was created in Power BI to support **time-based analysis** such as Monthly, Quarterly, Yearly and Financial Year reporting.

The Calendar table is connected with the transaction/fact table using the **Date** column and is used for time-intelligence calculations such as:

* YTD – Year-to-Date
* MTD – Month-to-Date
* QTD – Quarter-to-Date
* Previous Year Sales
* YoY Growth
* Monthly and Quarterly trends
* Financial Year analysis

### Calendar Table

The calendar table was created using:

```DAX
Calendar =
CALENDARAUTO(3)
```

The `3` represents **March as the last month of the financial year**, which means the financial year runs from **April to March**.

For example:

* April 2023 → FY 2023-2024
* December 2023 → FY 2023-2024
* March 2024 → FY 2023-2024
* April 2024 → FY 2024-2025

### Month Name

```DAX
Month_Name =
FORMAT('Calendar'[Date], "MMM")
```

This creates a short month name such as:

`Jan, Feb, Mar, Apr...`

### Month Sort

```DAX
Month Sort =
MONTH(EDATE('Calendar'[Date], -3))
```

The `EDATE()` function shifts the date by 3 months so that the financial year can be analyzed starting from **April** rather than January.

This column is used to maintain the required financial-year month order.

### Quarter

```DAX
Quarter =
"Q" & QUARTER(EDATE('Calendar'[Date], -3))
```

This creates financial quarters such as:

* Q1
* Q2
* Q3
* Q4

The date is shifted by 3 months so that the quarter calculation follows the **April–March financial year**.

### Year Month

```DAX
Years Month =
FORMAT('Calendar'[Date], "MMM-YYYY")
```

This creates a readable month-year label such as:

* Apr-2023
* May-2023
* Jun-2023

It is useful for monthly trend charts.

### Financial Year

For an April–March financial year, the FY column should be created as:

```DAX
FY =
VAR CurrentYear = YEAR('Calendar'[Date])
VAR CurrentMonth = MONTH('Calendar'[Date])

VAR FYStartYear =
    IF(
        CurrentMonth >= 4,
        CurrentYear,
        CurrentYear - 1
    )

RETURN
    FYStartYear & "-" & (FYStartYear + 1)
```

### Financial Year Logic

The formula checks the month:

* If month is **April to December**, the financial year starts in the current year.
* If month is **January to March**, the financial year started in the previous year.

Example:

| Date     | Financial Year |
| -------- | -------------- |
| Apr 2023 | FY 2023-2024   |
| Dec 2023 | FY 2023-2024   |
| Jan 2024 | FY 2023-2024   |
| Mar 2024 | FY 2023-2024   |
| Apr 2024 | FY 2024-2025   |

### Why the Calendar Table is Important

The Calendar table provides a consistent date structure for the entire Power BI model. It allows the report to analyze business performance across different time periods and supports DAX time-intelligence calculations.

The Calendar table is especially important for:

**YTD → MTD → QTD → Previous Year → YoY Growth → Financial Year Analysis**

This makes the Power BI report more suitable for **business performance and management reporting**.
