# SQL Import Example for Trade CSV Data

## Purpose

This document shows a simple example of how trade CSV data can be represented in SQL for learning, validation, and onboarding purposes.

It is intended as a beginner-friendly reference for understanding the CSV → SQL workflow.

## Alignment with ModelEarth Tradeflow Structure

This example follows the standard table structure used in ModelEarth tradeflow:

- trade → stores trade flow data (imports, exports, domestic)
- industry → represents economic sectors
- factor → represents environmental and economic factors
- trade_factor → links trade data with factor impacts

Reference:  
https://model.earth/exiobase/tradeflow/

## Example CSV source

A typical trade CSV file may come from a path like:

`trade-data/year/2019/IN/imports/trade.csv`

This represents:

- Year: 2019
- Country: IN (India)
- Trade flow: imports

## Example SQL table

Below is a simplified example aligned with ModelEarth tradeflow schema.

```sql
CREATE TABLE trade (
    id SERIAL PRIMARY KEY,
    country TEXT,
    year INTEGER,
    trade_type TEXT,
    industry_id INTEGER,
    value NUMERIC
);
