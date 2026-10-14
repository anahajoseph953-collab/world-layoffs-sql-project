# World Layoffs SQL Project

## 1. Project Overview

This project focuses on cleaning and analyzing a worldwide layoffs dataset using **MySQL**. The goal is to improve data quality, explore layoff trends, identify companies most affected by layoffs, and uncover patterns across industries, countries, company stages, and years.

The project is divided into two main parts:
- **Data Cleaning:** Preparing the dataset for accurate analysis.
- **Exploratory Data Analysis (EDA):** Investigating trends, rankings, and patterns in worldwide layoffs.

## 2. Tools Used

- MySQL
- MySQL Workbench
- SQL

## 3. Data Cleaning

The following data-cleaning steps were performed:

- Created staging tables to preserve the original dataset.
- Identified potential duplicate records using `ROW_NUMBER()` and `PARTITION BY`.
- Standardized inconsistent industry and country values.
- Converted text-based dates into the `DATE` data type.
- Investigated missing values and filled industry values where appropriate.
- Removed records missing both total layoffs and layoff percentage.
- Prepared the cleaned dataset for exploratory analysis.

## 4. Exploratory Data Analysis

SQL queries were used to explore the following questions:

- What was the maximum number of employees laid off in a single record?
- Which companies laid off 100% of their workforce?
- Which companies had the largest single layoff events?
- Which companies had the highest total layoffs?
- Which locations and countries recorded the most layoffs?
- Which industries were most affected?
- How did layoffs vary by company stage and year?
- Which companies ranked among the top three for layoffs in each year?
- How did total layoffs accumulate month by month?

SQL techniques included aggregate functions, filtering, grouping, sorting, Common Table Expressions (CTEs), window functions, and date functions.

## 5. Key Findings and Insights

The following are preliminary observations based on the analysis and comments made while exploring the dataset. Exact totals and rankings should be added after verifying the query results in MySQL Workbench.

### Company-Level Findings

- **Companies with 100% layoffs:** Filtering for `percentage_laid_off = 1` identified companies that reported laying off their entire workforce.
- **Startup closures:** Initial inspection suggested that many companies reporting 100% layoffs were startups that may have ceased operations.
- **Funding versus company outcomes:** Sorting these companies by `funds_raised_millions` helped investigate whether companies that raised substantial funding still experienced complete workforce reductions.
- **Largest layoff events:** The top-five query identified the largest individual layoff records in the dataset.
- **Highest total layoffs:** Aggregating layoffs by company made it possible to rank companies by their cumulative reported layoffs.

### Geographic Findings

- Grouping by `location` identified locations with the highest reported layoff totals.
- Grouping by `country` allowed comparisons of reported layoffs across countries.
- These results can help identify geographic concentrations of layoffs within the dataset.

### Industry and Company-Stage Findings

- Aggregating layoffs by `industry` showed which industries had the largest reported layoff totals.
- Grouping by `stage` allowed comparisons across company funding or development stages.
- These comparisons help explore whether layoffs were concentrated in particular industries or company stages.

### Yearly Trends

- Grouping layoffs by year revealed how annual totals changed over the period covered by the dataset.
- A `DENSE_RANK()` window function ranked companies by their yearly layoff totals.
- The ranking query returned the top three ranked companies for each year, including ties where applicable.

### Monthly Rolling Total

- Monthly aggregation showed how reported layoffs changed over time.
- A Common Table Expression (CTE) combined with a cumulative `SUM()` window function calculated the rolling total of layoffs.
- The rolling total helped show how reported layoffs accumulated from month to month.

## 6. Results Summary

Record the exact results from MySQL Workbench in the table below.

| Analysis | Result to Record |
|---|---|
| Maximum total layoffs in a single record | Add the value returned by `MAX(total_laid_off)` |
| Companies with 100% layoffs | Add the company names from the filtered results |
| Largest single layoff event | Add the top company and layoff count |
| Company with the highest total layoffs | Add the company name and total |
| Location with the highest layoffs | Add the location and total |
| Country with the highest layoffs | Add the country and total |
| Industry with the highest layoffs | Add the industry and total |
| Company stage with the highest layoffs | Add the stage and total |
| Top three companies by layoffs per year | Add company names, years, and totals |
| Month with the highest reported layoffs | Identify the month with the largest monthly total |
| Final rolling total | Add the last cumulative total returned by the query |

**Note:** The values in this table should be filled in using the actual query output. They are not inferred from the SQL statements alone.

## 7. SQL Concepts Demonstrated

- `SELECT`, `WHERE`, and `DISTINCT`
- `UPDATE` and `DELETE`
- `JOIN`
- Aggregate functions such as `MAX()`, `MIN()`, and `SUM()`
- `GROUP BY` and `ORDER BY`
- `LIMIT`
- `ROW_NUMBER()` and `DENSE_RANK()`
- Common Table Expressions (CTEs)
- Window functions and cumulative totals
- Date functions such as `YEAR()`
- String functions such as `SUBSTRING()`

## 8. Project Files

- `data_cleaning.sql` — SQL queries used to clean and standardize the dataset.
- `exploratory_data_analysis.sql` — SQL queries used to investigate layoff trends and summarize findings.

## 9. Key Learnings

Through this project, I practised:

- Cleaning and preparing data for analysis.
- Identifying potential duplicate records.
- Handling missing and inconsistent values.
- Using SQL aggregations to summarize large datasets.
- Applying CTEs and window functions to rank companies.
- Analyzing trends across time, locations, industries, and company stages.
- Translating query results into meaningful observations.

## 10. Conclusion

This project demonstrates how MySQL can be used to clean a real-world dataset and investigate patterns in worldwide layoffs. By combining data-cleaning techniques with exploratory analysis, the project provides a foundation for understanding company-level, industry-level, geographic, and time-based layoff trends.

## 11. Notes

This project is intended for educational purposes and as part of a data analytics portfolio. Findings reflect the dataset and its reporting limitations. Layoff totals do not necessarily represent every job loss, and correlations between funding, industry, and layoffs should not be interpreted as proof of causation.
