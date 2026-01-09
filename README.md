# Sales Analysis Power BI Dashboard

## Dashboard Overview

An interactive Power BI dashboard designed to analyze sales performance, identify trends, and generate actionable business insights for decision-makers.

---

## Objective

The primary objective of this dashboard is to help managers:

* Identify **best- and worst-performing products**
* Monitor **Sales, Net Sales, Profit, and Quantity trends** over time
* Analyze the **impact of discounts** on revenue and profitability
* Compare business performance across **two custom time periods**
* Visualize **sales distribution across regions and cities**

---

## Dataset Description

The data model follows a **star schema**, with a central **Fact table** connected to multiple **dimension tables**.

### Fact Table

Key columns include:

* Order ID
* Product ID
* Date
* City
* Quantity
* Sales
* Net Sales
* Profit

### Dimension Tables

* **Product** – Product details and pricing
* **Promotion** – Discount information
* **Customer** – Customer Details(Name,city,pincode,mail)

---

## Tools & Skills Used

* **Power BI Desktop**
* **Power Query (M)** for data cleaning, profiling, and transformation
* **DAX** for calculated columns and measures (Sales, Net Sales, Profit, time intelligence, period comparison)
* **Data modeling** using relationships and star schema principles
* **Visual design & data storytelling** best practices

---

## Project Steps – What I Did

### 1. Data Profiling and Preparation (Power Query)

* Performed **column profiling** to understand data distribution, distinct values, and potential primary keys.
* Checked **column quality** to identify errors, empty values, and inconsistencies.
* Corrected **data types** for numeric, date, and text fields to ensure reliable analysis and accurate modeling.

---

### 2. Data Transformation and Fact Table Enrichment

* Observed that key business fields such as **PricePerUnit, TotalSales, Discount%, DiscountValue, and NetSales** were missing or null in the Fact table.
* Merged the **Fact table** with the **Product dimension** using `ProductID` to retrieve `PricePerUnit`.
* Created a custom column:

  **Total Sales = PricePerUnit × Quantity**
* Retrieved **Discount%** from the Promotion dimension.
* Replaced null discount values with **0**, since discounts are not applicable to all products.
* Created:

  * **Discount Value = (Total Sales × Discount%)/100**
  * **Net Sales = Total Sales − Discount Value**

---

### 3. Creating Profit and Business Metrics

* Since Profit was not directly available, defined **Profit as 10 percentage of Net Sales**.
* Created a calculated column / measure:

  **Profit = 0.1 × Net Sales**
* Used **Net Sales, Profit, Quantity, and Discount** as the core metrics across all visuals.

---

### 4. Modeling Orders and Total Order Count

* Identified that each row in the Fact table represents an **order line**.
* Ensured `OrderID` had the correct data type and logical consistency.
* Built a **card visual** using a **distinct count of OrderID** to display the total number of unique orders.

---

### 5. Visual Design and Analysis

#### Product Performance

* Created **Top 5 and Bottom 5 product visuals** based on:

  * Sales
  * Profit
  * Quantity sold

#### Trend Analysis

* Used **line charts** to show trends in Sales across:

  * Daily
  * Monthly
  * Quarterly
  * Yearly levels

#### Relationship Between Sales and Profit (Scatter Chart)

    Created a scatter chart with Sales on the X-axis and Profit on the Y axis.    

    helping visualize how profit varies with sales volume.  

#### Discount Analysis

* Built bar charts to analyze **average discount offered** across different discount categories.

#### Geographic Analysis

* Added a **map visual** to represent Sales distribution across cities and regions.

#### Order-Level View

* Designed a **detailed table visual** containing key fields for record-level drill-down and validation.

---

### 6. Period-over-Period Comparison (Two Custom Date Ranges)

* Created two separate Date tables:

  * `DateTable1`
  * `DateTable2`
* Established one **active relationship** and one **inactive relationship** with the Fact table.
* Added **two date slicers**, allowing users to select two independent time periods.
* Built a **clustered column chart** to compare:

  * Sales
  * Profit
  * Quantity
    across the selected periods.

#### DAX Logic (Conceptual)

* Used `CALCULATE`, `ALL`, and `USERELATIONSHIP` to correctly evaluate metrics for each period.

Example:

Total Profit – Period 1 =
CALCULATE(
SUM(FactTable[Profit]),
ALL('DateTable1'),
USERELATIONSHIP('DateTable1'[Date], FactTable[Date])
)

---

## Key Insights from the Dashboard

* Clear visibility into **top- and bottom-performing products**, enabling better inventory and pricing decisions.
* Strong understanding of **sales  trends over time**, supporting forecasting and planning.
* Quantifiable impact of **discount strategies** on revenue and profitability.
* Ability to perform **side-by-side performance comparison** between two custom time periods.
* Geographic insights highlighting **high- and low-performing cities and regions**.

---

## Conclusion

This Sales Analysis Power BI Dashboard provides a comprehensive, interactive, and decision-oriented view of business performance. By combining strong data modeling, DAX-driven metrics, and intuitive visuals, the dashboard empowers stakeholders to make informed, data-driven decisions efficiently.


* snapshot of page1
<img width="1314" height="734" alt="Image" src="https://github.com/user-attachments/assets/125cce29-a2f5-4c49-8549-1388f2f2fc19" />


* snapshotof page 2
<img width="1335" height="728" alt="Image" src="https://github.com/user-attachments/assets/de93d296-5a03-43b0-9138-e724eba3684d" />


* snapshot of  page 3
<img width="1223" height="688" alt="Image" src="https://github.com/user-attachments/assets/81729b82-ab57-444e-8f35-0b43f5e6e05d" />


* snapshot of page 4
<img width="1294" height="724" alt="Image" src="https://github.com/user-attachments/assets/92919a70-3e2a-400c-9f09-9b7b9aff1ce0" />
