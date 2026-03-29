# 📘 Power BI Technical Assessment – Instructions

This project was completed as part of a Power BI technical assessment.

The objective was to evaluate the ability to perform end-to-end data analysis using Power BI, including data ingestion, transformation, modeling, DAX calculations, and visualization.

---

## 📂 1. Data Loading

### Dimensions
- Load all dimension tables from a folder containing Excel and CSV files  
- Ensure all primary keys are unique  

### Sales (Fact Table)
- Combine multiple yearly sales files into a single table  

### Requirements
- Adding a new sales file should automatically be included on refresh  
- Removing a file should not break the model  

---

## 🧹 2. Data Preparation

- Split the `Location` column into:
  - Country  
  - Town  

- Ensure appropriate data types are applied for:
  - Geographic fields (for mapping visuals)  
  - Date fields  

- Clean and standardize inconsistent date formats  

---

## 🌍 3. Data Modeling

- Create a unique geographic key (`GeoKey`) in the Geography table  
- Map each sales record to a corresponding geography entry  

- Build relationships between:
  - Sales (fact table)  
  - Product  
  - Geography  
  - Category and Subcategory  
  - Sales Representative  
  - Calendar table  

- Ensure the model follows a **star schema design**  

---

## 🧩 4. Data Transformation

- Standardize ID fields with formats such as `ID-XX`  
- Create a reusable function to remove prefixes  
- Apply transformations across relevant dimension tables  

---

## 📊 5. DAX Calculations

Create measures for:

### Core Metrics
- Total Revenue  
- Total Cost  
- Gross Profit  
- Gross Profit %  

### Analytical Metrics
- Average Sales per Day  
- Market Share %  

### Time Intelligence
- Year-to-Date (YTD)  
- Year-to-Date Last Year (YTD LY)  
- Month-to-Date (MTD)  
- Moving Annual Total (MAT)  

---

## 📈 6. Visualization

- Build a one-page dashboard  
- Present insights across:
  - Time  
  - Product  
  - Geography  

- Apply visualization best practices and clear layout  

---

## 🎯 Objective

Demonstrate:

- Strong data modeling skills  
- Ability to handle real-world data challenges  
- Proficiency in DAX and Power Query  
- Clear and effective data storytelling  