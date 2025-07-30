# Sales & Inventory Performance

This project is a real-world Business Intelligence (BI) analysis focused on retail sales and inventory performance across different locations and customer demographics. Built using **Power BI**, **SQL Server**, and **Excel Power Query**, the dashboard reveals insights that drive actionable business decisions.

## 📑 Table of Contents

1. [Background and Overview](#1-background-and-overview)  
2. [Data Structure Overview](#2-data-structure-overview)  
3. [Executive Summary](#3-executive-summary)  
4. [Insight Deep Dive: 2023 Performance Drop](#4-insight-deep-dive-2023-performance-drop)  
5. [Recommendation & Professional Storytelling](#5-recommendation--professional-storytelling)

---

## Project Structure

- `Dataset`: [Download Dataset](https://microsoft.com)
- `Power BI File`: [Download PBIX File](https://microsoft.com)
- `Portfolio PDF`: [Download Full PDF Report](https://microsoft.com)
- `Assets`:

   <img src="https://github.com/user-attachments/assets/d6e7faf8-b984-4891-9576-989082fb4661" alt="Data Pipeline Screenshot" width="450"/>

---

## 1. Background and Overview

In this project, I developed a Sales Performance Dashboard to provide real-time insights into revenue growth, profit margins, and demographic-driven sales behavior across multiple locations.

**Key Objectives:**
- Track sales trends over multiple years
- Evaluate profit efficiency against cost
- Identify age group segments driving revenue
- Compare sales & profitability by city/location
- Support executive decisions on growth strategy and market targeting

**Key Insights:**
- Strong YoY Revenue Growth of 32.6%, reaching £4.25M
- High profitability with 74% profit margin, totaling £3.15M
- Middle-aged adults account for 68.02% of sales
- Equal revenue and profit distribution across Paris, London, and Accra
- 2023 shows sharp decline in sales

**Strategic Recommendations:**
- Focus on middle-aged adult campaigns
- Investigate 2023 performance drop
- Expand in consistently performing cities
- Align sales with seasonal demand

- ---

## 2. Data Structure Overview

**Dataset Composition:**
- Fields: TransactionDate, Product, AgeGroup, Location
- Metrics: Revenue, Profit, TotalCost
- Time dimensions: Weekday, Month, Year, Quarter

**ETL Workflow:**
- **Excel Power Query**: Cleaned nulls, standardized dates, added age groups  
  ![Power Query Cleaning](https://github.com/user-attachments/assets/14c7c4db-3939-4e0f-af75-d36d1763a30a)
- **SQL Server**:

```sql
-- Calculate Sales and Cost
SELECT
    SbS.*,
    CAST(SbS.quantity_sold AS FLOAT) * CAST(SbS.unit_price AS FLOAT) AS Sales,
    CAST(SbS.quantity_sold AS FLOAT) * CAST(PR.current_cost AS FLOAT) AS Cost
FROM JendolSuperStore.dbo.[Sales by Store] AS SbS
INNER JOIN JendolSuperStore.dbo.Product AS PR
    ON SbS.product_id = PR.product_id;

  
 -- Calculate Age and Age Group
SELECT
    *,
    DATEDIFF(YEAR, birthdate, GETDATE()) AS Age,
    CASE
        WHEN DATEDIFF(YEAR, birthdate, GETDATE()) <= 39 THEN 'Young Adult'
        WHEN DATEDIFF(YEAR, birthdate, GETDATE()) <= 59 THEN 'Middle-Age Adult'
        ELSE 'Old Adult'
    END AS Age_Group
FROM JendolSuperStore.dbo.Customer;

```
- **Power BI**: Star schema model, built with DAX for YoY %, Profit Margin, Total Revenue, Sales Growth  
  ![Sales Dashboard M](https://github.com/user-attachments/assets/c34f807e-ee16-422d-a96c-7dba3084f757)  
  ![Sales Dashboard Y](https://github.com/user-attachments/assets/6234e7a8-18fb-4fad-959a-f86b1c714b40)

---

## 3. Executive Summary

This dashboard offers a clear, high-level overview of business performance, helping decision-makers quickly grasp key insights:
- **Overall financial performance** including revenue, cost, and profit
- **Year-over-year growth trends** from 2020 to 2023
- **Customer purchasing patterns** across different age groups
- **Performance consistency** across three international locations

---

## 4. Insight Deep Dive: 2023 Performance Drop

**Upon examining the Sales Growth Trend Over Time, the line chart clearly shows:**
- A steady incline from **2020 (£1.05M)** through **2022 (£1.04M)**
- A drastic fall to **£0.0M in 2023**, despite consistent cost baselines

**Possible Causes:**
- Incomplete or missing data
- Operational interruptions or market changes
- Faulty source file import

**Next Steps:**
- Validate 2023 data integrity
- Check SQL extract logs and Excel imports

---

## 5. Recommendation

This dashboard presents a compelling narrative:
- Consistent revenue growth (except 2023)
- Dominant demographic: Middle Age Adults
- Balanced city-wide profitability

**Next Strategic Steps:**
- Re-audit 2023 data entries
- Strengthen outreach to core demographics
- Improve location-specific planning
- Automate anomaly detection in dashboards

---

## 🙋‍♂️ Author
**Bernard Joseph**  
Data Analyst  
[www.linkedin.com/in/bernard-joseph-oyakhilome](#) | [https://thenalyst3global.github.io/Sales-Inventory_Analysis/#1-background-and-overview](#) | [jozefbernardonline@gmail.com](#)
