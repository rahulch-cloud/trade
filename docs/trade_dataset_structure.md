# Trade Dataset Structure

## Overview

This document explains how the trade dataset is organized in the repository.  
Understanding this structure helps contributors locate CSV files and import them into SQL tables.

---

## Main Data Directory

Trade data is stored under:

trade-data/

Inside this directory, the dataset is organized by year, country, and trade flow.

Example structure:

trade-data/
   year/
      2019/
         AU/
         BR/
         CA/
         CN/
         DE/
         FR/
         GB/
         IN/
         IT/
         JP/
         KR/

Each folder represents a country code.

Examples:

AU = Australia  
IN = India  
CA = Canada  

---

## Trade Flow Types

Inside each country folder, trade flows are separated into different categories:

imports/  
exports/

Example:

trade-data/year/2019/IN/imports/trade.csv

This represents:

Year: 2019  
Country: India  
Trade Flow: Imports

---

## CSV Data

Each CSV file typically contains trade relationships between industries.

Example columns may include:

source_industry  
target_industry  
trade_value  

These values represent the trade flow between industries.

---

## Mapping to SQL

When importing CSV files into SQL, the data may be mapped into a table like this:

CREATE TABLE trade_data (
    id INTEGER PRIMARY KEY,
    year INTEGER,
    country_code TEXT,
    trade_flow TEXT,
    source_industry TEXT,
    target_industry TEXT,
    trade_value NUMERIC
);

This allows the dataset to be queried using SQL for analytics and validation.

---

## Why This Structure Exists

The dataset structure allows:

• separation by year  
• filtering by country  
• modular CSV imports  
• scalable SQL data loading
