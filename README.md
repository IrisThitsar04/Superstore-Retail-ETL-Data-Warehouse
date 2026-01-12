# Superstore Retail Sales Data Warehouse

## Project Overview

This project presents the **design and implementation of a retail data warehouse** for analysing Superstore sales data. The solution transforms raw transactional data into a structured analytical model to support **reporting and business insight generation**.

The project demonstrates an **end-to-end data warehousing pipeline**, covering source data ingestion, schema transformation, dimensional modelling, ETL design, and analytical reporting using industry-standard tools.

## Objectives

The primary goals of the project are to:

- Design a **scalable and maintainable data warehouse** using dimensional modelling
- Enable analysis of **customer behaviour, product performance, employee efficiency, and returns**
- Support **OLAP-style analysis** and automated reporting
- Demonstrate best practices in **ETL design, schema design, and derived business logic**

## Source Data

The warehouse is built using the **Superstore dataset**, sourced from three CSV files:

- superstore.csv
- superstore_employees.csv
- superstore_returns.csv

The dataset contains structured retail data across multiple business domains, including:

- Orders and order line items
- Products and categories
- Customers and addresses
- Employees and regions
- Shipping methods
- Returns

## Data Architecture Overview

The solution uses a **three-layer architecture**:

### 1. Source Layer
Raw CSV files loaded into a base database (SuperStore_dataset) without modification.

### 2. Normalized Staging Layer
A relational schema (OrderManagementDB) designed to:
- Reduce redundancy
- Enforce referential integrity
- Prepare data for dimensional modelling

Core tables include:

- CustomerProfile, CustomerAddress
- Employee
- Products
- ShipMode
- Orders, OrderLine
- OrderReturns

### 3. Data Warehouse Layer
A **star schema** implemented in the SalesInsights_DW warehouse for analytical querying and reporting.

## Star Schema Design

At the centre of the warehouse is the **SalesFact** table, surrounded by five dimension tables:

### Dimension Tables

- **CustomerDim** : customer attributes, tenure, and loyalty tier
- **EmployeeDim** : employee performance and sales contribution
- **ProductDim** : product categories, subcategories, and margin classification
- **DateDim** : full calendar dimension supporting order and ship dates
- **ShipModeDim** : shipping method reference data

### Fact Table

- **SalesFact** captures transaction-level metrics, including:
    - Sales, quantity, discount, and profit
    - Derived metrics such as NetSales and ProfitMargin
    - Flags for returns, discounts, order size, and profitability

This structure supports fast analytical queries and flexible reporting.

## Derived Business Logic

To support deeper analysis, several derived attributes were implemented, including:

- **Customer tenure and loyalty tier**
- **Net sales and profit margin**
- **Discount and high-discount flags**
- **Order size categorisation**
- **Return indicators**
- **Employee performance tiers**

These derived fields are calculated during ETL to ensure consistency across reports and dashboards.

## ETL Strategy

The ETL process was implemented using **SSIS in Visual Studio 2022**, following a modular design:

- One ETL package per dimension and fact table
- Dimension tables loaded first, followed by the fact table
- Lookup transformations used to resolve surrogate keys
- Derived business logic applied during transformation

Key ETL goals:

- Ensure data quality and referential integrity
- Apply business rules consistently
- Support maintainability and traceability

## Reporting

To demonstrate analytical capability, the warehouse also supports **SSRS reports**.

### SSRS Reports

- Product Subcategory ROI Analysis by Margin Type
- Orders and Returns by Region, Category, and Subcategory
- Employee Performance Overview
- Product Category Performance and Discount Analysis

These outputs validate the warehouse design and demonstrate practical business use cases.

## Technology Stack

- **Database**: SQL Server
- **ETL**: SSIS (Visual Studio 2022)
- **Reporting**: SSRS
- **Modelling**: Dimensional modelling (Star Schema)
  
## Key Takeaway

This project demonstrates the **end-to-end design of a retail data warehouse**, from raw data ingestion to analytical reporting. It highlights how structured data modelling, well-designed ETL pipelines, and derived business logic can support meaningful business insights in a retail analytics context.
