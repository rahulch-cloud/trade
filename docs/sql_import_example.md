# SQL Import Example for Trade CSV Data

## Purpose
This document shows a simple example of how trade CSV data can be represented in SQL
for learning, validation, and onboarding purposes.

It is intended as a beginner-friendly reference for understanding the CSV → SQL workflow.

## Example CSV source
A typical trade CSV file may come from a path like:

`trade-data/year/2019/IN/imports/trade.csv`

This represents:
- Year: 2019
- Country: IN (India)
- Trade flow: imports

## Example SQL table
Below is a simplified example of how trade CSV data could be loaded into a SQL table.

```sql
CREATE TABLE trade_example (
    id INTEGER PRIMARY KEY,
    year INTEGER,
    country_code TEXT,
    trade_flow TEXT,
    source_industry TEXT,
    target_industry TEXT,
    trade_value NUMERIC
);
