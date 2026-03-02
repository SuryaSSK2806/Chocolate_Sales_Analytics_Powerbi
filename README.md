# Chocolate_Sales_Analytics_Powerbi
Power BI dashboard analyzing chocolate sales performance using a star-schema data model. Includes revenue KPIs, product category contribution, geographic distribution, sales trends, and salesperson performance insights. Demonstrates data modeling, DAX measures, and executive-level dashboard design best practices.
# 📊 Chocolate Sales Analytics Dashboard (Power BI)

## 🚀 Project Overview
This project delivers an end-to-end Power BI reporting solution that analyzes chocolate product sales using shipment-level transactions and product master data.  
The dashboard converts raw Excel datasets into clear business insights across revenue performance, product mix, geography, trends, and salesperson contribution.

**Primary objective:** build a clean data model + professional visuals that support decision-making (not just charts).

---

## 📁 Repository Contents
- **Power BI Report Export (PDF):** `chocolate bars -CA.pdf`
- **Dataset (Excel):** `sample-chocolate-shipments-data-all-Apr-2025.xlsx`
- **Documentation:** `README.md`

> If you're viewing the PDF, it contains the complete report pages and visuals.

---

## 🗂️ Data Sources
### 1) Shipments (Fact Table)
Transaction-level shipping and revenue data, including:
- `ShipmentID`
- `PID` (Product ID)
- `GID` (Geography ID)
- `Shipdate`
- `Amount` (Sales / Revenue)
- `Boxes`
- `Order_Status`
- `Delivered_Flag`
- `Sales_Category`

### 2) Products (Dimension Table)
Product reference data, including:
- `PID` (Primary Key)
- `Product`
- `Category` (Bars / Bites / Other)
- `Cost_per_box`

### 3) Locations (Dimension Table)
Geography reference data, including:
- `GID` (Primary Key)
- `Geo` (Country)
- `Region`

---

## 🧠 Data Model & Relationships (Star Schema)
The model follows a star-schema design:
- **Products (1) → Shipments (*)** via `PID`
- **Locations (1) → Shipments (*)** via `GID`

This approach ensures:
- Accurate aggregations
- Clean filtering behavior
- Scalable reporting structure
- Consistent category and region slicing

---

## 🧮 Key DAX Measures
A core measure was created to standardize revenue calculations:

```DAX
Total Sales = SUM('shipments (2)'[Amount])
