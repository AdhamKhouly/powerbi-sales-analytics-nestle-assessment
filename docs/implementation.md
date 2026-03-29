# 🛠️ Implementation Approach

⏱️ Completed in: 120 minutes

This document outlines the approach taken to design and implement a scalable and portable Power BI solution, transforming raw data into a structured model and an executive-ready dashboard.

This implementation focuses on building a **reusable and production-oriented solution**, rather than a one-off report.

---

## 📂 1. Data Ingestion Strategy

### Dynamic Folder-Based Loading

Instead of loading files individually, a **folder-based ingestion approach** was implemented:

- Used Power BI **Folder connector** to load all sales files  
- Combined multiple yearly files into a single fact table  
- Ensured robustness:
  - Removing a file does not break the model  
  - Adding a new file is automatically included upon refresh  

---

### Parameterization for Portability

To make the solution portable across different environments:

- Created parameters:
  - `SalesFolder`
  - `DimensionsFolder`
- Replaced static file paths with parameters in queries  

This allows the report to be reused on any machine without modifying the data source.

---

## 🧹 2. Data Cleaning & Transformation

### Location Normalization

- Split the `Location` column into:
  - Country  
  - Town  
- Ensured correct data types for geographic analysis and mapping  

---

### Date Handling

The original date field contained inconsistencies that resulted in parsing errors.

Solution:
- Converted the date column to text  
- Split into:
  - Day  
  - Month  
  - Year  
- Reconstructed a valid date column  
- Created a Calendar table to support time intelligence  

---

### ID Standardization

Some dimension tables contained IDs in the format:

`ID-1`, `ID-2`, etc.

To standardize:

- Created a reusable Power Query function `fnCleanID`  
- Removed the `"ID-"` prefix  
- Applied the function to:
  - SalesRep  
  - SubCategories  

---

## 🌍 3. Data Modeling

### GeoKey Creation

- Created a unique `GeoID` in the Geography table using an index (starting from 1)  
- Merged Sales with Geography using:
  - Country  
  - Town  
- Expanded the merged column to include `GeoID` in the Sales table  

---

### Star Schema Design

Implemented a clean star schema:

- **Fact Table**
  - Sales  

- **Dimension Tables**
  - Product  
  - Geography  
  - SalesRep  
  - SubCategories  
  - Categories  
  - Calendar  

Relationships were defined as one-to-many and set as active.

This ensures:
- Efficient filtering  
- Scalable model design  
- Clear data relationships  

---

## 📊 4. DAX Measures

A dedicated **Measures Table** was created to organize all calculations and maintain a clean model.

---

### Core Metrics

- Total Revenue  
- Total Cost  
- Gross Profit  
- Gross Profit %  

---

### Analytical Metrics

- Average Sales per Day  
- Market Share %  

Market Share was calculated by dividing:
- Revenue filtered by country  
- By total revenue across all countries  

---

### Time Intelligence

Implemented key time-based measures:

- Year-to-Date (YTD)  
- Year-to-Date Last Year (YTD LY)  
- Month-to-Date (MTD)  
- Moving Annual Total (MAT)  

These rely on the Calendar table for accurate date filtering.

---

## 📈 5. Dashboard Design

The dashboard was structured into four analytical views:

- **Executive Overview** → high-level KPIs and trends  
- **Time Analysis** → performance over time and growth patterns  
- **Product Analysis** → product-level revenue, cost, and profitability  
- **Geography Analysis** → regional performance and market share  

---

### Design Principles

- KPI-first layout for quick executive insights  
- Consistent visual design and formatting  
- Clear separation of analytical dimensions  
- Focus on business-relevant metrics  

---

## ⚠️ Key Challenges

- Handling Power BI privacy restrictions when combining multiple sources  
- Resolving date parsing issues across inconsistent formats  
- Implementing dynamic ingestion within a limited time frame  

---

## 💡 Key Decisions

- Used parameterization to improve portability and reusability  
- Implemented a star schema to enhance performance and clarity  
- Created reusable transformation functions for cleaner data processing  

---

## 🔄 Future Improvements

Given more time, the following enhancements could be implemented:

- Incremental refresh for handling larger datasets  
- Additional drill-through pages for deeper analysis  
- More advanced KPIs (e.g., variance vs targets, forecasting)  

---

## 🚀 Outcome

Delivered a fully functional and scalable Power BI solution within 120 minutes, capable of:

- Automatically handling new data files  
- Supporting business-level analysis  
- Providing actionable insights across time, product, and geography  