# Periodic Table Database

This project is part of the freeCodeCamp Relational Database Curriculum. It involves building a Bash script to query a PostgreSQL database containing information about chemical elements. The project emphasizes database normalization, SQL data manipulation, Bash scripting, and Git version control.

## 📋 Project Overview

The objective was to take a raw database of chemical elements and fix various schema errors, normalize the data structure, and develop a command-line tool (`element.sh`) that provides element details based on atomic number, symbol, or name.

## 🛠️ Database Schema & Fixes

The database underwent a significant refactor to ensure data integrity and normalization:

- **Renaming Columns**: 
  - `weight` → `atomic_mass`
  - `melting_point` → `melting_point_celsius`
  - `boiling_point` → `boiling_point_celsius`
- **Constraints**: 
  - Added `NOT NULL` and `UNIQUE` constraints to `symbol` and `name`.
  - Set `atomic_number` in `properties` as a Foreign Key referencing `elements`.
- **Normalization**:
  - Created a `types` table to store distinct element types.
  - Linked `properties` to `types` using a `type_id` foreign key.
  - Dropped the redundant `type` column from the `properties` table.
- **Data Cleanup**:
  - Capitalized all element symbols correctly.
  - Removed trailing zeros from `atomic_mass` by converting the type to `DECIMAL`/`REAL`.
  - Removed non-existent test data (Atomic Number 1000).
  - Added missing elements: **Fluorine (9)** and **Neon (10)**.

## 💻 The Script

The `element.sh` script is a Bash program that interfaces with the PostgreSQL database.

### Usage
```bash
./element.sh <argument>
