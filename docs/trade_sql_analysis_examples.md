# Trade SQL Analysis Examples

## Overview

This document provides example SQL queries that demonstrate how trade data can be analyzed after importing CSV files into a SQL database.

These queries help contributors understand the dataset and explore trade patterns between countries and industries.

---

## Example Table Structure

Trade CSV data can be mapped into a SQL table like this:

CREATE TABLE trade_data (
    id INTEGER PRIMARY KEY,
    year INTEGER,
    country_code TEXT,
    trade_flow TEXT,
    source_industry TEXT,
    target_industry TEXT,
    trade_value NUMERIC
);

---

## Total Trade Value by Country

This query calculates the total trade value for each country.

SELECT
    country_code,
    SUM(trade_value) AS total_trade_value
FROM trade_data
GROUP BY country_code
ORDER BY total_trade_value DESC;

---

## Total Imports by Country

This query calculates total imports for each country.

SELECT
    country_code,
    SUM(trade_value) AS total_imports
FROM trade_data
WHERE trade_flow = 'imports'
GROUP BY country_code
ORDER BY total_imports DESC;

---

## Total Exports by Country

This query calculates total exports for each country.

SELECT
    country_code,
    SUM(trade_value) AS total_exports
FROM trade_data
WHERE trade_flow = 'exports'
GROUP BY country_code
ORDER BY total_exports DESC;

---

## Top Trading Industries

This query identifies industries with the highest trade value.

SELECT
    source_industry,
    SUM(trade_value) AS total_trade
FROM trade_data
GROUP BY source_industry
ORDER BY total_trade DESC
LIMIT 10;

---

## Industry-to-Industry Trade Relationships

This query shows trade flows between industries.

SELECT
    source_industry,
    target_industry,
    SUM(trade_value) AS trade_total
FROM trade_data
GROUP BY source_industry, target_industry
ORDER BY trade_total DESC
LIMIT 20;

---

## Trade Trends by Year

This query analyzes trade values across different years.

SELECT
    year,
    SUM(trade_value) AS total_trade
FROM trade_data
GROUP BY year
ORDER BY year;

---

## Why These Queries Are Useful

These example queries allow contributors to analyze:

• total trade by country  
• import and export patterns  
• key trading industries  
• relationships between industries  
• trade trends across years

These queries provide a starting point for deeper analysis of the trade dataset.
