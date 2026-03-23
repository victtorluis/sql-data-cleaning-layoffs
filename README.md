# World Layoffs - SQL Data Cleaning Project

## Overview
This project focuses on cleaning and standardizing a raw dataset of global layoffs. Using **MySQL**, I performed a series of data cleaning steps to ensure the data is accurate, consistent, and ready for explore.

## Project Workflow
The project was divided into four main stages:

1. **Checking for duplicates and removing them:** Used `ROW_NUMBER` and `CTEs` to identify duplicate rows across all columns. Since the table lacked a unique ID, I created a staging table with a temporary `row_num` column to bypass MySQL's deletion limitations and safely remove duplicates.

2. **Standardizing the data:** - Applied `TRIM` to remove extra whitespaces from company names.
   - Unified industry names (e.g., merging 'Crypto Currency' and 'Crypto' into a single category).
   - Fixed location and country inconsistencies (e.g., removing trailing dots from 'United States').

3. **Checking date column and converting string to date type:** Used `STR_TO_DATE` to convert the date text into a standard SQL format (`YYYY-MM-DD`) and then modified the column type using `ALTER TABLE`.

4. **Handling Null/Blank values and cleaning up:** - Populated missing 'Industry' data by joining the table with itself (Self Join) where other records for the same company existed.
   - Deleted rows where both 'total_laid_off' and 'percentage_laid_off' were null, as they provided no value for analysis.
   - Dropped temporary columns used during the cleaning process.

## Technologies Used
* **Database:** MySQL
* **Tool:** MySQL Workbench
* **Key SQL Concepts:** CTEs, Window Functions (`ROW_NUMBER`), Self Joins, Data Type Casting (`ALTER TABLE`), String Manipulation (`TRIM`, `LIKE`).
