# Seven Sages Brewing Company Data Model and Power BI Report

This project focuses on creating a comprehensive data model and Power BI report for Seven Sages Brewing Company to help them leverage their data for informed decision-making. The goal is to transform disjointed data sources into actionable insights regarding product popularity and profitability.

## Key Tasks Performed:

**1. Data Acquisition and Cleaning (Power Query)**

The following data files were used in this project:

* `CFO Metrics Tracker.xlsx`
* `Customer List (as of FY2021).txt`
* `SSBC Product Offerings.pdf`
* `USD-CAD Exchange Rates.csv`
* Monthly Sales Logs (located in the `Monthly Sales Logs/` subdirectory)

These files were sourced from Udacity and are available in the `Files/` folder of this repository.

* **ETL with Power Query:**

Power Query was utilized to perform data cleaning and preprocessing on the acquired datasets. Key steps included:

* **Merging Monthly Sales Files in Power Query:**

The following steps were performed in Power Query to combine the twelve monthly sales log files into a single `Sales Logs` query:

1.  **Source Data from Folder:**
    * The `Folder.Files` function was used to retrieve a list of all files within the specified directory containing the monthly sales logs.

2.  **Select Relevant Columns:**
    * The table was filtered to retain only the "Content" (binary file data) and "Name" (file name) columns. This removes unnecessary columns.

3.  **Invoke Custom Function to Read Excel Files:**
    * A custom function, `"Read Excel File"`, was invoked for each row, using the "Content" column to read the Excel file's data. The result was added as a new "Tables" column containing the table data from each Excel file.

4.  **Expand Tables Column.**
    
5.  **Filter Rows for Table Kind:**
    * The table was filtered to retain only rows where the "Tables.Kind" column indicated "Table," ensuring only the actual data tables from the Excel files were included.

6.  **Select Data Column:**
    * Only the "Tables.Data" column, which contained the data from each individual sheet, was kept.

7.  **Invoke Custom Function to Read Excel Sheet Table:**
    * Another custom function, `"read excel sheet table"`, was invoked on the "Tables.Data" column to extract the specific sheet's table data. The results were added to the "Sheet" column.

8.  **Expand Sheet Column:**
    * The "Sheet" column, containing the sales data, was expanded to create individual columns for "CustID," "ProdID," "Date," "Currency," and "Qty."

9.  **Remove Redundant Columns.**
    
10. **Change Data Types.**
    
* **Merging Customer and Product Information:**
    * `Customer List (as of FY2021).txt` and `SSBC Product Offerings.pdf` were merged into the `Products` query, incorporating all relevant product attributes.

**Note:** Seven Sages Brewing's fiscal year begins on October 1st and ends on September 30th. Therefore, a transaction on September 20th, 2020, falls within FY 2020, while a transaction on October 20th falls within FY 2021.

## Date Table Creation

A dynamic date table was generated using DAX Calculations, designed to automatically adjust its range based on the start and end dates of the `Sales Logs` fact table. This date table includes the following standard fields:

* Calendar month number
* Calendar year
* Fiscal year
* Fiscal quarter number
* Fiscal quarter year

**2. Data Modeling (Power BI)**

* **Create Data Tables:**
    * Imported the cleaned and transformed data from Power Query into Power BI data tables.
* **Establish Relationships:**
    * Identified primary and foreign keys to define relationships between tables.
    * Created accurate relationships based on these keys, reflecting the business logic.
    * Ensured the relationships were optimized for data analysis and reporting.

**3. DAX Measures and Calculations**

* **Create DAX Measures:**
    * Developed key performance indicators (KPIs) relevant to Seven Sages Brewing's business, such as total sales, gross profit, and profit margin.
   
**4. Report Creation (Power BI)**
![Sales and Gross Profit Margin by Product](Data Model for Seven Sages Brewing Company/images/Sales&GPM By product.JPG)


