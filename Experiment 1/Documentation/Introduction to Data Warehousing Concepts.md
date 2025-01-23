<div style='text-align:center; color: #00B050'>
<h1 style="font-size: 16pt">Author: Madhurima Rawat</h1>
<h2 style="font-size: 14pt">Introduction to Data Warehousing Concepts</h2>

<h3 style="font-size: 12pt">This experiment aims to introduce the fundamental concepts of data warehousing, focusing on its architecture, components, and processes, including ETL (Extract, Transform, Load), data modeling, and Online Analytical Processing (OLAP).</h3>
</div>

## **Definition of Key Concepts**

### **1. Data Warehousing**

A **Data Warehouse** is a centralized repository designed for storing, managing, and analyzing large volumes of structured data. It supports decision-making processes by enabling fast and efficient querying and reporting.

- **Features**:
  - Subject-Oriented: Focused on specific business areas like sales or finance.
  - Integrated: Combines data from multiple sources.
  - Non-volatile: Data remains stable and unchanged over time.
  - Time-variant: Provides historical data for analysis.

---

### **2. ETL Process**

**ETL (Extract, Transform, Load)** is a key process in data warehousing that involves:

- **Extract**: Retrieving data from various source systems (e.g., databases, files, APIs).
- **Transform**: Cleaning, filtering, and formatting data to meet the warehouse’s requirements.
- **Load**: Inserting the transformed data into the data warehouse.

---

### **3. Data Modeling**

**Data Modeling** involves creating the logical and physical design of a data warehouse. The two main schemas used are:

- **Star Schema**: A central fact table connected to dimension tables.
- **Snowflake Schema**: A variation of the star schema where dimensions are normalized.

---

### **4. OLAP (Online Analytical Processing)**

**OLAP** refers to techniques used for multidimensional data analysis in a data warehouse. It supports:

- **Slice and Dice**: Focusing on specific data subsets.
- **Drill-Down/Drill-Up**: Navigating between granular and aggregated data levels.
- **Pivoting**: Reorienting data dimensions for new perspectives.

---

## **Working Diagrams**

### **1. Data Warehousing Architecture**

```plaintext
+------------------+    +-------------------+    +----------------+
| Source Systems   | -> | ETL Processes     | -> | Data Warehouse |
| (Databases, APIs |    | (Extract, Transform, |    | (Centralized)  |
|  Files, etc.)    |    |  Load)             |    |                |
+------------------+    +-------------------+    +----------------+
                                 |
                                 V
                         +----------------+
                         | OLAP Tools     |
                         | (Reports,      |
                         | Dashboards,    |
                         | Analytics)     |
                         +----------------+
```

<br>

<p align="center">
    <img src="https://daxg39y63pxwu.cloudfront.net/images/blog/how-to-design-a-data-warehouse/Data_Warehouse_Architecture_Design.png" alt="Data Warehouse Architecture Design" height="400px">
</p>

---

### **2. ETL Process**

```plaintext
+----------------+    +----------------+    +----------------+
| Extract        | -> | Transform      | -> | Load           |
| (Source Data)  |    | (Clean &       |    | (Data Warehouse|
|                |    | Format)        |    | Storage)       |
+----------------+    +----------------+    +----------------+
```

<br>

<p align="center">
    <img src="https://www.getdbt.com/assets/uploads/etl-diagram.png" alt="ETL" height="400px">
</p>

---

### **3. Star Schema for Data Modeling**

```plaintext
                   +-------------+
                   | Time         |
                   +-------------+
                          |
                          |
+-------------+    +-------------+    +-------------+
| Product     |    | Fact Table  |    | Customer    |
+-------------+ -> | (Sales Data)| <- +-------------+
                          |
                   +-------------+
                   | Store        |
                   +-------------+
```

<br>

<p align="center">
    <img src="https://slideplayer.com/slide/13066760/79/images/8/Example+of+Star+Schema+item+branch+time+Sales+Fact+Table+time_key.jpg" alt="Star Schema" height="400px">
</p>

A star schema is a data modeling technique commonly used in data warehousing. It consists of:

1. **Fact Table**: The central table that contains quantitative data (measures) for analysis. It is typically large and has foreign keys linking to dimension tables.
2. **Dimension Tables**: Smaller tables that store descriptive attributes (context) about the measures in the fact table. These provide insights like "who," "what," "where," and "when."

The star schema is called so because its structure resembles a star, with the fact table at the center and the dimension tables radiating outwards.

---

### **4. OLAP Operations**

```plaintext
+-------------+     +-------------+     +-------------+
| Slice       |     | Dice        |     | Drill-Down  |
| (Subset     |     | (Multiple   |     | (Detailed   |
| Analysis)   |     | Subsets)    |     | View)       |
+-------------+     +-------------+     +-------------+
```

<br>

<p align="center">
    <img src="https://smartboost.com/wp-content/uploads/2020/06/OLAP-Blog-image-01-2048x994.jpg" alt="OLAP" height="400px">
</p>

### OLAP Cube Explanation

An **OLAP (Online Analytical Processing) cube** is a multidimensional data structure designed for high-performance analytical queries in data warehouses. It organizes data into **dimensions** (e.g., time, product, geography) and **measures** (e.g., sales, revenue) to allow users to analyze data from multiple perspectives. OLAP cubes simplify complex queries by pre-aggregating and summarizing data, enabling operations like slicing (filtering a single dimension), dicing (analyzing multiple dimensions), roll-ups (summarizing data), and drill-downs (exploring detailed data).

These cubes are commonly used in business intelligence to support decision-making. They offer fast query responses for complex data exploration, making them ideal for applications like sales forecasting, trend analysis, and performance monitoring.

---

### Real-World Example: Product Sales Analysis

Suppose a company sells products like beverages, snacks, and food. An OLAP cube might include:

- **Product Dimension**: Categories (Beverages, Snacks, Food) and Subcategories (Juice, Soda, Chips).
- **Time Dimension**: Year, Quarter, Month, Day.
- **Location Dimension**: Country, State, City.
- **Measure**: Sales Revenue, Units Sold.

For instance, you can use the cube to:

1. Slice: View **beverage sales** in **January 2024**.
2. Dice: Compare sales for **snacks vs. beverages** in **California** across **Q1 2023**.
3. Roll-Up: Aggregate sales by **country** instead of individual states.
4. Drill-Down: Analyze detailed sales of **soda in Los Angeles**.

This structure empowers organizations to explore data quickly and make informed decisions based on historical and aggregated insights.
