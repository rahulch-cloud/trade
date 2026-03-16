# Trade Data Insights

## Overview

This document demonstrates how trade data can be analyzed after importing CSV datasets into a SQL database.

The queries below highlight useful analytical perspectives such as top trading countries, industry relationships, and trade trends over time.

---

## Top Exporting Countries

This query identifies countries with the highest total export value.

SELECT
    country_code,
    SUM(trade_value) AS total_exports
FROM trade_data
WHERE trade_flow = 'Export'
GROUP BY country_code
ORDER BY total_exports DESC
LIMIT 10;

---

## Top Importing Countries

This query shows which countries import the largest trade value.

SELECT
    country_code,
    SUM(trade_value) AS total_imports
FROM trade_data
WHERE trade_flow = 'Import'
GROUP BY country_code
ORDER BY total_imports DESC
LIMIT 10;

---

## Strongest Industry Trade Relationships

This query highlights which industries trade most with each other.

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

This query analyzes how trade value changes over time.

SELECT
    year,
    SUM(trade_value) AS total_trade
FROM trade_data
GROUP BY year
ORDER BY year;

---

## Key Analytical Insights

Using the queries above, analysts can explore:

- global trade leaders
- import vs export dominance
- strongest industry relationships
- trade growth trends over time

These insights can support economic analysis, supply chain research, and sustainability modeling.

---

## Future Enhancements

Further analysis could include:

- regional trade comparisons
- industry dependency mapping
- trade network visualization
- anomaly detection in trade flows
