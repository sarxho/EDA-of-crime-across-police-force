# Police Force Street-Level Crime Analysis (Kent, Surrey, Met & Essex)

## Overview
This project analyses **UK street-level crime data** across four police forces — **Metropolitan Police, Kent Police, Surrey Police, and Essex Police** — covering **September 2023 to September 2025**.

The purpose of the project is to clean and combine monthly crime datasets, then perform **Exploratory Data Analysis (EDA)** to uncover:
- Regional differences in crime volume
- Monthly and yearly crime trends
- Most common crime categories by area
- Crime outcome patterns (case resolution insights)
- Seasonal crime patterns across forces

---

## Dataset
- **Source:** UK Police open street-level crime data (monthly CSV files)
- **Time range:** Sep 2023 – Sep 2025
- **Regions:** Metropolitan, Kent, Surrey, Essex
- **Granularity:** Street-level (includes location names + coordinates when available)

---

## Project Workflow

### 1) Data Cleaning & Preprocessing
The cleaning stage focuses on creating a consistent dataset that is reliable for analysis.

**Key preprocessing steps:**
- Imported and combined **monthly CSV files (2023–2025)** for each police force
- Standardised formatting/structure across datasets
- Removed **duplicate rows**
- Dropped the `Context` column (empty across files)
- Converted `Month` into a proper **datetime** format
- Extracted time features:
  - `Year`, `Month_number`, `Month_name`
- Filled missing categorical values:
  - `Crime type` → `"Unknown"`
  - `Last outcome category` → `"Unknown"`
- Cleaned location text (removed repetitive prefixes like `"On or near"`)
- Preserved missing coordinate values (`Longitude`, `Latitude`) as `NaN` for later spatial filtering
- Saved cleaned datasets:
  - One CSV per force
  - One final combined dataset for EDA

---

### 2) Exploratory Data Analysis (EDA)
The EDA is structured around five key questions:

1. **Regional Comparison**
   - Which police force recorded the highest and lowest overall crime counts?

2. **Temporal Trends**
   - How has crime changed over time by police force?
   - Includes monthly trend lines and a year-to-year comparison:
     - Year 1: Sep 2023 – Sep 2024  
     - Year 2: Oct 2024 – Sep 2025  

3. **Crime Type Distribution**
   - What are the most common crime categories overall?
   - How do the top 10 crime types vary between police forces?

4. **Crime Outcomes**
   - What are the proportions of outcome categories by force?
   - “Unknown” outcomes are evaluated and excluded for clearer comparisons
   - Stacked bar charts used to show outcome distributions

5. **Seasonal & Monthly Patterns**
   - Heatmap shows how crime levels vary by month and police force
   - Highlights seasonal increases and decreases over the two-year period

---

## Tools & Libraries
- **Python**
- **Pandas**, **NumPy**
- **Matplotlib**, **Seaborn**
- **Glob**, **OS** (file handling + automation)

---

## Outputs
Cleaned datasets are saved in the `Clean_policeforce_data/` folder:

- `Metropolitan_all_months.csv`
- `Kent_all_months.csv`
- `Surrey_all_months.csv`
- `Essex_all_months.csv`
- `All_Forces_Cleaned_2023_2025.csv`

---

## How to Run
1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
