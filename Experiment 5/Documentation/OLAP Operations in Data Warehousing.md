<div style='text-align:center; color: #00B050'>
<h1 style="font-size: 16pt">Author: Madhurima Rawat</h1>
<h2 style="font-size: 14pt">OLAP Operations in Data Warehousing</h2>

<h3 style="font-size: 12pt">OLAP operations such as slicing, dicing, drill-down, drill-up, and pivoting were applied to analyze predefined data in a data warehouse.</h3>
</div>

---

## **OLAP (Online Analytical Processing)**

## **What is OLAP?**

OLAP (Online Analytical Processing) is a computing approach that enables users to perform multidimensional analysis of business data. It helps in decision-making by allowing complex queries, aggregations, and drill-downs on large datasets efficiently.

Unlike traditional transactional databases (OLTP), which focus on real-time transactions, OLAP systems are optimized for querying and reporting.

- **OLTP (Online Transaction Processing)** → Handles frequent, real-time transactions (e.g., bank transactions, online orders).
- **OLAP (Online Analytical Processing)** → Handles complex analytical queries on historical data (e.g., sales trends, forecasting).

### **Key Features of OLAP:**

- **Multidimensional Analysis** – Data is stored in a structured format like a cube for fast querying.
- **Drill-Down & Roll-Up** – Navigate data at different levels (e.g., yearly → monthly → daily sales).
- **Pivoting & Slicing** – View data from different perspectives and filter specific segments.
- **Fast Query Performance** – Aggregated data provides quicker insights than traditional databases.

---

## **How OLAP Works**

OLAP organizes data into an **OLAP Cube**, a multidimensional data model where data is categorized into multiple dimensions for analysis.

**Example:** A retail company might analyze sales data using three dimensions:

- **Time** (Year → Quarter → Month → Day)
- **Products** (Category → Subcategory → SKU)
- **Location** (Region → Country → Store)

This allows users to ask complex questions like:

- What were the total sales of electronics in North America in Q4?

<p align="center">  
    <img src="https://cdn.infodiagram.com/c/243800/operations-olap-cube.webp" alt="OLAP Cube" height="300px">  
</p>

---

## **Real-World Use Cases of OLAP**

### **1. Retail Industry**

Retail companies use OLAP to analyze customer purchase trends, optimize inventory, and improve sales forecasting.

**Example:**  
A supermarket chain wants to identify which products sell the most in different seasons. Using OLAP, they can compare sales across different time periods, regions, and product categories.

### **2. Financial Analysis**

Banks and financial institutions use OLAP for risk analysis, fraud detection, and investment performance tracking.

**Example:**  
A bank needs to evaluate loan default rates across different customer segments. OLAP helps in analyzing past loan data, interest rates, and borrower demographics.

### **3. Healthcare Analytics**

Hospitals and healthcare providers use OLAP for patient record analysis, treatment effectiveness, and resource allocation.

**Example:**  
A hospital can track patient admission trends and determine peak times for different departments, helping in staff allocation.

### **4. Supply Chain Management**

Manufacturing and logistics companies use OLAP for demand forecasting, supplier performance evaluation, and inventory optimization.

**Example:**  
A car manufacturer wants to analyze delays in different regions and identify bottlenecks in the supply chain.

### **5. Marketing and Customer Insights**

Businesses use OLAP to analyze customer behavior, campaign effectiveness, and revenue trends.

**Example:**  
An e-commerce company wants to compare the impact of different marketing campaigns on customer engagement and sales.

---

## **OLAP vs. ETL**

OLAP often works in combination with ETL (Extract, Transform, Load) processes, which are used to collect and clean data before analysis.

### **ETL Process Overview:**

<p align="center">  
    <img src="https://www.getdbt.com/assets/uploads/etl-diagram.png" alt="ETL Diagram" height="300px">  
</p>

1. **Extract** – Data is gathered from multiple sources such as databases, files, and APIs.
2. **Transform** – Data is cleaned, structured, and converted into a format suitable for analysis.
3. **Load** – The processed data is stored in a data warehouse, ready for OLAP queries.

---

## **Additional OLAP Visualizations**

### **OLAP Analysis Workflow:**

<p align="center">  
    <img src="https://smartboost.com/wp-content/uploads/2020/06/OLAP-Blog-image-02-2048x1799.jpg" alt="OLAP Workflow" height="300px">  
</p>

### **OLAP Cube Implementation in SSAS (SQL Server Analysis Services):**

<p align="center">  
    <img src="https://www.codeproject.com/KB/database/658912/SSAS_Basic_Image.png" alt="OLAP in SSAS" height="300px">  
</p>

### **Multidimensional Analysis Example:**

<p align="center">  
    <img src="https://cdn.educba.com/academy/wp-content/uploads/2019/11/Operations-in-OLAP.png" alt="OLAP Cube Operations" height="300px">  
</p>

---

## **Conclusion**

OLAP is a powerful tool for business intelligence and data analysis, enabling organizations to make data-driven decisions efficiently. Whether in retail, finance, healthcare, or supply chain management, OLAP helps businesses uncover patterns, trends, and insights from large datasets.

---

## **OLAP in MySQL**

### **Step 1: Create and Use the Database**

#### **Input:**

```sql
CREATE DATABASE olap;
USE olap;
```

#### **Command Breakdown:**

- `CREATE DATABASE olap;` → Creates a new database named `olap` to store and manage data.
- `USE olap;` → Switches to the newly created `olap` database to perform further operations.

#### **Output:**

```
Query OK, 1 row affected (0.08 sec)
Database changed
```

This confirms that the database was successfully created and is now in use.

---

### **Step 2: Create the Sales Table**

#### **Input:**

```sql
CREATE TABLE Sales (
    Product VARCHAR(50),
    Region VARCHAR(50),
    Year INT,
    Sales_Amount DECIMAL(10,2)
);
```

#### **Command Breakdown:**

- Creates a table `Sales` with the following fields:
  - `Product` → Stores product names like "Laptop" and "Phone".
  - `Region` → Represents sales regions such as "North" and "South".
  - `Year` → Stores the year in which the sales occurred.
  - `Sales_Amount` → Holds the revenue generated in decimal format.

#### **Output:**

```
Query OK, 0 rows affected (0.06 sec)
```

This confirms that the table has been created successfully.

---

### **Step 3: Insert Sample Data**

#### **Input:**

```sql
INSERT INTO Sales VALUES
('Laptop', 'North', 2022, 50000),
('Laptop', 'South', 2022, 45000),
('Phone', 'North', 2022, 30000),
('Phone', 'South', 2022, 32000),
('Laptop', 'North', 2023, 52000),
('Laptop', 'South', 2023, 47000),
('Phone', 'North', 2023, 31000),
('Phone', 'South', 2023, 33000);
```

#### **Command Breakdown:**

- Inserts eight rows into the `Sales` table, covering different products, regions, and years.

#### **Output:**

```
Query OK, 8 rows affected (0.01 sec)
Records: 8  Duplicates: 0  Warnings: 0
```

This confirms that all records were successfully added.

---

### **Step 4: Query Sales Data for a Specific Region**

#### **Input:**

```sql
SELECT * FROM Sales WHERE Region = 'North';
```

#### **Command Breakdown:**

- Fetches all sales records where the `Region` is "North".

#### **Output:**

```
+---------+--------+------+--------------+
| Product | Region | Year | Sales_Amount |
+---------+--------+------+--------------+
| Laptop  | North  | 2022 |     50000.00 |
| Phone   | North  | 2022 |     30000.00 |
| Laptop  | North  | 2023 |     52000.00 |
| Phone   | North  | 2023 |     31000.00 |
+---------+--------+------+--------------+
```

#### **Output Breakdown:**

- Shows all sales made in the "North" region.
- Confirms that laptops and phones were sold in both 2022 and 2023.
- Helps in analyzing sales performance specific to a region.

---

### **Step 5: Query Specific Sales Data**

#### **Input:**

```sql
SELECT * FROM Sales
WHERE Region = 'North' AND Year = 2022 AND Product = 'Laptop';
```

#### **Command Breakdown:**

- Filters sales data for:
  - **Region** = North
  - **Year** = 2022
  - **Product** = Laptop

#### **Output:**

```
+---------+--------+------+--------------+
| Product | Region | Year | Sales_Amount |
+---------+--------+------+--------------+
| Laptop  | North  | 2022 |     50000.00 |
+---------+--------+------+--------------+
```

#### **Output Breakdown:**

- Isolates a single row showing that **50,000** worth of laptops were sold in **North** in **2022**.
- Useful for targeted sales analysis based on product, region, and time frame.

---

### **Step 6: Aggregate Sales Data by Year**

#### **Input:**

```sql
SELECT Year, SUM(Sales_Amount) AS Total_Sales
FROM Sales
GROUP BY Year;
```

#### **Command Breakdown:**

- Groups data by `Year`.
- Uses `SUM(Sales_Amount)` to calculate total sales for each year.

#### **Output:**

```
+------+-------------+
| Year | Total_Sales |
+------+-------------+
| 2022 |   157000.00 |
| 2023 |   163000.00 |
+------+-------------+
```

#### **Output Breakdown:**

- Shows total sales in **2022** was **157,000** and in **2023** it was **163,000**.
- Helps in identifying year-over-year growth or decline in sales.

---

### **Step 7: Aggregate Sales by Year and Product**

#### **Input:**

```sql
SELECT Year, Product, SUM(Sales_Amount) AS Total_Sales
FROM Sales
GROUP BY Year, Product;
```

#### **Command Breakdown:**

- Groups sales data by both `Year` and `Product`.
- Uses `SUM(Sales_Amount)` to find total revenue per product each year.

#### **Output:**

```
+------+---------+-------------+
| Year | Product | Total_Sales |
+------+---------+-------------+
| 2022 | Laptop  |    95000.00 |
| 2022 | Phone   |    62000.00 |
| 2023 | Laptop  |    99000.00 |
| 2023 | Phone   |    64000.00 |
+------+---------+-------------+
```

#### **Output Breakdown:**

- Laptops and phones both showed an increase in sales from **2022 to 2023**.
- Used to analyze product performance trends over time.

---

### **Step 8: Compare Sales Across Years**

#### **Input:**

```sql
SELECT Product,
       SUM(CASE WHEN Year = 2022 THEN Sales_Amount ELSE 0 END) AS Sales_2022,
       SUM(CASE WHEN Year = 2023 THEN Sales_Amount ELSE 0 END) AS Sales_2023
FROM Sales
GROUP BY Product;
```

#### **Command Breakdown:**

- Uses `CASE` statements to conditionally sum sales amounts for each year.
- Groups data by `Product`.

#### **Output:**

```
+---------+------------+------------+
| Product | Sales_2022 | Sales_2023 |
+---------+------------+------------+
| Laptop  |   95000.00 |   99000.00 |
| Phone   |   62000.00 |   64000.00 |
+---------+------------+------------+
```

#### **Output Breakdown:**

- Laptops sales increased from **95,000** in **2022** to **99,000** in **2023**.
- Phone sales increased from **62,000** to **64,000** in the same period.
- Useful for understanding product growth trends across different years.

---

### **Purpose of These Queries**

1. **Data Storage and Retrieval**

   - Efficiently storing structured sales data in MySQL for later analysis.

2. **Filtering and Querying**

   - Extracting specific data based on conditions like region, year, and product.

3. **Aggregation for Trend Analysis**

   - Summarizing total sales per year and per product.

4. **Year-over-Year Comparisons**

   - Tracking performance improvements or declines over time.

5. **Business Decision Support**
   - Helping managers and analysts identify trends, forecast demand, and optimize sales strategies.

This structured OLAP analysis in MySQL helps businesses gain deeper insights into their sales data, supporting data-driven decision-making.
