# 📊 Key Business Measures & DAX Calculations

This project uses DAX measures to analyze **sales, profit, orders, customer behavior and year-over-year business growth**.

These measures were created to provide management with important KPIs and performance indicators.

---

## 1. Total Net Sales

```DAX
Total Net Sales =
SUM(Orders[Net_Sales])
```

### Purpose

Calculates the total revenue generated after applying the required sales adjustments.

### Business Use

Used as the main sales KPI for:

* Sales performance
* AOV
* Profit Margin
* YoY Sales Growth
* YTD / MTD / QTD analysis

---

## 2. Total Profit

```DAX
Total Profit =
SUM(Orders[Profit])
```

### Purpose

Calculates the total profit generated from sales.

### Business Use

Helps management understand whether revenue is actually generating profit.

---

## 3. Total Orders

```DAX
Total Orders =
DISTINCTCOUNT(Orders[order_id])
```

### Purpose

Counts unique orders.

### Business Use

Used to measure:

* Order volume
* Customer purchasing activity
* AOV
* YoY Order Growth

`DISTINCTCOUNT` is used because the same order can contain multiple order-item rows.

---

# ⏱️ Time Intelligence Measures

## 4. Total MTD

```DAX
Total MTD =
TOTALMTD(
    [Total Net Sales],
    'Calendar'[Date]
)
```

### MTD = Month-to-Date

Calculates sales from the beginning of the current month up to the selected date.

### Business Use

Useful for monitoring the current month's progress.

Example:

If the selected date is **15 August**, MTD shows sales from:

**1 August → 15 August**

---

## 5. Total QTD

```DAX
Total QTD =
TOTALQTD(
    [Total Net Sales],
    'Calendar'[Date]
)
```

### QTD = Quarter-to-Date

Calculates sales from the beginning of the current quarter up to the selected date.

### Business Use

Helps management track current-quarter performance.

---

## 6. Total YTD

```DAX
Total YTD =
TOTALYTD(
    [Total Net Sales],
    'Calendar'[Date]
)
```

### YTD = Year-to-Date

Calculates sales from the beginning of the year up to the selected date.

### Business Use

Useful for tracking cumulative yearly performance.

Because this project uses an **April–March financial year**, the Calendar table is configured for financial-year analysis.

---

# 👥 Customer Analysis

## 7. Repeat Customers

```DAX
Repeat Customers =
COUNTROWS(
    FILTER(
        SUMMARIZE(
            Orders,
            Orders[customer_id],
            "OrderCount", DISTINCTCOUNT(Orders[order_id])
        ),
        [OrderCount] >= 2
    )
)
```

### Purpose

Counts customers who have placed **at least two orders**.

### Business Use

Helps measure customer retention and repeat purchasing behavior.

A higher number of repeat customers generally indicates stronger customer loyalty.

---

# 💰 Customer & Profitability KPIs

## 8. AOV

```DAX
AOV =
DIVIDE(
    [Total Net Sales],
    [Total Orders]
)
```

### AOV = Average Order Value

Shows the average amount spent per order.

### Formula

**AOV = Total Net Sales ÷ Total Orders**

### Business Use

Helps management understand how much revenue is generated from an average order.

---

## 9. Profit Margin %

```DAX
Profit Margin % =
DIVIDE(
    [Total Profit],
    [Total Net Sales]
)
```

### Purpose

Measures what percentage of sales becomes profit.

### Formula

**Profit Margin = Profit ÷ Net Sales**

### Business Use

A company may have high sales but low profit. Therefore, Profit Margin helps evaluate the quality of revenue.

---

# 📅 Previous Year Analysis

## 10. Previous Year AOV

```DAX
Previous Year AOV =
CALCULATE(
    [AOV],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

### Purpose

Calculates AOV for the equivalent period in the previous year.

### Business Use

Allows management to compare current customer spending with last year's performance.

---

## 11. Previous Year Orders

```DAX
Previous Year Orders =
CALCULATE(
    [Total Orders],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

### Purpose

Calculates the number of orders for the same period last year.

### Business Use

Used to measure growth or decline in order volume.

---

## 12. Previous Year Profit

```DAX
Previous Year Profit =
CALCULATE(
    [Total Profit],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

### Purpose

Calculates profit for the corresponding previous-year period.

### Business Use

Helps compare profitability year over year.

---

## 13. Previous Year Profit Margin %

```DAX
Previous Year Profit Margin % =
DIVIDE(
    [Previous Year Profit],
    [Previous Year Sales]
)
```

### Purpose

Calculates the previous year's profit margin.

### Business Use

Used to compare current profitability against the previous year.

---

## 14. Previous Year Repeat Customers

```DAX
Previous Year Repeat Customers =
CALCULATE(
    [Repeat Customers],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

### Purpose

Calculates repeat customers for the equivalent period last year.

### Business Use

Helps analyze whether customer retention is improving or declining.

---

## 15. Previous Year Sales

```DAX
Previous Year Sales =
CALCULATE(
    [Total Net Sales],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

### Purpose

Calculates sales for the equivalent period in the previous year.

### Business Use

This is the base measure for calculating YoY Sales Growth.

---

# 📈 Year-over-Year Growth Measures

## 16. AOV YoY Growth %

```DAX
AOV YoY Growth % =
DIVIDE(
    [AOV] - [Previous Year AOV],
    [Previous Year AOV]
)
```

### Purpose

Measures the percentage change in average order value compared with the previous year.

### Business Use

Shows whether customers are spending more or less per order.

---

## 17. Repeat Customer YoY Growth %

```DAX
RC YoY Growth % =
DIVIDE(
    [Repeat Customers] - [Previous Year Repeat Customers],
    [Previous Year Repeat Customers]
)
```

### Purpose

Measures growth or decline in repeat customers.

### Business Use

Useful for evaluating customer retention and loyalty.

---

## 18. Order YoY Growth %

```DAX
YoY Order Growth % =
DIVIDE(
    [Total Orders] - [Previous Year Orders],
    [Previous Year Orders]
)
```

### Purpose

Measures year-over-year change in total orders.

### Business Use

Helps management understand whether order volume is growing or declining.

---

## 19. Profit YoY Growth %

```DAX
YoY Profit Growth % =
DIVIDE(
    [Total Profit] - [Previous Year Profit],
    [Previous Year Profit]
)
```

### Purpose

Measures the percentage change in profit compared with the previous year.

### Business Use

Shows whether business profitability is improving or declining.

---

## 20. Profit Margin YoY Change

```DAX
YoY Profit Margin Change =
[Profit Margin %] - [Previous Year Profit Margin %]
```

### Purpose

Measures the change in profit margin compared with the previous year.

### Business Use

Helps identify whether the company is becoming more or less profitable.

Unlike normal YoY growth, this is a **percentage-point change**.

---

## 21. Sales YoY Growth %

```DAX
YoY Sales Growth % =
DIVIDE(
    [Total Net Sales] - [Previous Year Sales],
    [Previous Year Sales]
)
```

### Purpose

Measures the percentage change in sales compared with the previous year.

### Business Use

One of the most important management KPIs for evaluating business growth.

---

# 📊 Business KPI Summary

| Measure                  | Business Question                        |
| ------------------------ | ---------------------------------------- |
| Total Net Sales          | How much did we sell?                    |
| Total Profit             | How much profit did we make?             |
| Total Orders             | How many orders did we receive?          |
| AOV                      | How much does an average order generate? |
| Profit Margin %          | How profitable are our sales?            |
| Repeat Customers         | How many customers purchased again?      |
| MTD                      | How are we performing this month?        |
| QTD                      | How are we performing this quarter?      |
| YTD                      | How are we performing this year?         |
| Previous Year Sales      | What were sales last year?               |
| Previous Year Profit     | What was profit last year?               |
| YoY Sales Growth %       | Are sales growing or declining?          |
| YoY Profit Growth %      | Is profit growing or declining?          |
| AOV YoY Growth %         | Are customers spending more per order?   |
| RC YoY Growth %          | Is customer retention improving?         |
| YoY Profit Margin Change | Is profitability improving?              |

## 🎯 Management Value

These DAX measures transform raw e-commerce transactions into actionable business insights.

The measures allow management to answer questions such as:

* Are sales growing?
* Is profit growing faster or slower than sales?
* Are customers returning to purchase again?
* Is the average order value increasing?
* How are current sales performing against last year?
* How much sales have been generated MTD, QTD and YTD?
* Is the company's profit margin improving?
* Is customer retention improving?

This makes the dashboard useful for **business performance monitoring, management reporting and data-driven decision-making**.
