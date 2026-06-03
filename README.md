# Travel Agency Sales Analysis Using SQL

## Project Overview

This project analyzes travel agency sales performance using SQL. The dataset contains agency-level sales transactions across multiple states, cities, sales teams, regional heads, and national heads.

The objective is to derive actionable business insights and demonstrate practical SQL skills commonly used in Data Analyst roles.

---

## Business Objectives

* Identify top-performing salesmen and agencies.
* Compare sales performance across states.
* Analyze FSC and LCC sales contributions.
* Evaluate regional and national leadership performance.
* Rank salesmen and agencies using analytical SQL techniques.

---

## Dataset Information

### Table Name

`daily_tct_cnt`

### Key Columns

| Column Name     | Description                |
| --------------- | -------------------------- |
| Agency_Name     | Travel agency name         |
| Agency_Id       | Unique agency identifier   |
| SalesMan        | Sales representative       |
| State_Head      | State manager              |
| Regional_Head   | Regional manager           |
| National_Head   | National manager           |
| State_Name      | State location             |
| City_Name       | City location              |
| Transaction_Cnt | Number of transactions     |
| Ticket_Count    | Number of tickets sold     |
| Total_Sales     | Total revenue generated    |
| FSC             | Full Service Carrier sales |
| LCC             | Low Cost Carrier sales     |

---

# SQL Analysis Performed

## 1. Dataset Exploration

Understanding dataset structure before analysis.

```sql
SELECT *
FROM daily_tct_cnt
LIMIT 10;
```

---

## 2. Top 10 Salesmen by Revenue

```sql
SELECT
    salesman,
    SUM(Total_Sales) AS total_sales
FROM daily_tct_cnt
GROUP BY salesman
ORDER BY total_sales DESC
LIMIT 10;
```

### Insight

Identifies the highest revenue-generating salesmen.

---

## 3. Top 5 Salesmen in Delhi Under Specific National Head

```sql
SELECT
    salesman,
    SUM(Total_Sales) AS total_sales
FROM daily_tct_cnt
WHERE National_Head = 'B Sunil Kumar'
AND State_Name = 'Delhi'
GROUP BY salesman
ORDER BY total_sales DESC
LIMIT 5;
```

### Insight

Evaluates performance within a specific leadership hierarchy.

---

## 4. Highest Ticket-Selling Agency in Odisha

```sql
SELECT
    Agency_Name,
    Ticket_Count
FROM daily_tct_cnt
WHERE Agency_Name LIKE 'A%'
AND State_Name = 'Odisha'
ORDER BY Ticket_Count DESC
LIMIT 1;
```

### Insight

Identifies the strongest agency among a targeted group.

---

## 5. FSC Sales Analysis by State

```sql
SELECT
    State_Name,
    SUM(FSC) AS FSC_Sales
FROM daily_tct_cnt
GROUP BY State_Name
ORDER BY FSC_Sales DESC;
```

### Insight

Compares Full Service Carrier performance across states.

---

## 6. State-wise Salesman Performance

```sql
SELECT
    State_Name,
    salesman,
    SUM(Total_Sales) AS Total_Sales
FROM daily_tct_cnt
GROUP BY State_Name, salesman
ORDER BY State_Name, Total_Sales DESC;
```

### Insight

Measures sales contribution at state level.

---

## 7. Top Salesman in Each State

```sql
SELECT *
FROM (
    SELECT
        State_Name,
        salesman,
        SUM(Total_Sales) AS Total_Sales,
        RANK() OVER (
            PARTITION BY State_Name
            ORDER BY SUM(Total_Sales) DESC
        ) AS Rank_Value
    FROM daily_tct_cnt
    GROUP BY State_Name, salesman
) t
WHERE Rank_Value = 1;
```

### Insight

Identifies the best-performing salesman in every state.

---

# SQL Skills Demonstrated

### Core SQL

* SELECT
* WHERE
* ORDER BY
* GROUP BY
* LIMIT

### Aggregation

* SUM()
* COUNT()
* AVG()
* MIN()
* MAX()

### Analytical SQL

* Window Functions
* RANK()
* PARTITION BY

### Business Reporting

* Sales Performance Analysis
* KPI Reporting
* State-wise Analysis
* Leadership Performance Tracking

---

# Key Learnings

* Performed exploratory data analysis using SQL.
* Built business-focused reporting queries.
* Applied aggregation functions for performance measurement.
* Used window functions to solve ranking problems.
* Generated actionable insights from transactional sales data.

---

# Tools Used

* SQL
* MySQL
* GitHub

---

# Future Enhancements

* Common Table Expressions (CTEs)
* Advanced Window Functions
* Sales Trend Analysis
* Percentage Contribution Reports
* Dashboard Development using Power BI

---

# Author

**Hridayendu Goswami**

Aspiring Data Analyst

Skills: SQL | Python | Pandas | Data Analysis | Data Visualization

GitHub Portfolio Project
