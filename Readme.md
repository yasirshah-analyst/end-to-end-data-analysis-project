# 🎵 Concert Tour Data Cleaning & Analysis (Excel Project)


## 📌 Project Overview

This project focuses on cleaning and analyzing a messy concert tour dataset to extract meaningful business insights. The dataset was transformed from a raw, inconsistent format into a structured and analysis-ready dataset using Excel.

The final output includes a fully interactive dashboard showcasing key metrics such as revenue trends, top artists, and performance analysis.

---

## 🎯 Project Objectives
- Clean and standardize a messy dataset
- Handle missing values, duplicates, and formatting issues
- Transform raw data into structured format
- Perform exploratory data analysis (EDA)
- Build an interactive Excel dashboard
- Generate actionable insights

---

## 🔎 Data Analysis Process

This project follows a structured 6-phase data analysis workflow:

### 1️⃣ Ask
Defined the business questions this analysis aims to answer:
- Which artists/tours generate the highest revenue?
- Does the number of shows correlate with total revenue?
- How has tour revenue changed over time?
- Which artists earn the most per show (efficiency vs. volume)?

### 2️⃣ Prepare
- Sourced the dataset from Kaggle: *Dirty Dataset for Data Cleaning Practice*
- Reviewed data structure, column types, and license (CC0: Public Domain)
- Identified known data quality issues before starting cleaning (see "Issues in Raw Data" below)

### 3️⃣ Process (Data Cleaning)
- Removed unnecessary columns (`Peak`, `All Time Peak`, `Ref`)
- Fixed duplicate/broken values in the `Rank` column
- Cleaned currency symbols, commas, and footnotes from `Actual_Gross` and `Adjusted_Gross`
- Removed special symbols (†, ‡, *) from `Tour_Title`
- Standardized the `Years` column into `Start_Year` / `End_Year`, converted to numeric
- Verified no remaining nulls, duplicates, or text-as-number fields before moving to analysis

### 4️⃣ Analyze
- Added helper columns: `Tour_Duration`, `Revenue_per_Show`
- Built PivotTables to answer each business question:
  - Top Earning Artists
  - Top Tours
  - Shows vs Revenue
  - Revenue Over Time
  - Average Gross Comparison
- Cross-checked pivot table outputs against raw totals to confirm accuracy

### 5️⃣ Share
- Visualized each PivotTable using Pivot Charts
- Combined all charts into a single interactive Excel dashboard with KPIs, trend charts, and slicers (Artist, Year)
- Documented every cleaning and analysis step with screenshots for transparency and reproducibility

### 6️⃣ Act (Insights & Recommendations)
- Highlighted top-performing artists/tours to inform where future scheduling or investment focus could go
- Identified whether high-revenue tours rely on volume (more shows) or premium pricing (higher revenue/show)
- Surfaced year-over-year revenue trends to flag growth or decline periods worth investigating further

---


## 🛠 Tools Used
- Excel
- Pivot Tables
- Excel Formulas (VALUE, IF, LEFT, RIGHT)
- Data Cleaning Techniques
- Data Visualization (Charts & Dashboard)

---

## 📁 Project Structure

```
end-to-end-data-analysis-project/
│
├── analysis/
│   └── screenshot/
│       ├── end_year_1.png
│       ├── revenue_per_show.png
│       ├── start_year.png
│       ├── tour_duration.png
│       └── year_range.png
│
├── cleaning/
│   └── screenshot/
│       ├── adjusted_gross_number.png
│       ├── average_gross_number.png
│       ├── end_year_value.png
│       ├── extra_columns.png
│       ├── gross_footnotes.png
│       ├── gross_number.png
│       ├── rank_duplicate_1.png
│       ├── rank_duplicate_2.png
│       ├── start_year_trim.png
│       ├── start_year_value.png
│       ├── tour_title_trim.png
│       └── tourtitle_symbol.png
│
├── dashboard/
│   └── screenshot/
│       └── dashboard.png
│
├── data/
│   ├── raw/
│   │   ├── files/
│   │   │   └── concert_tour_raw.csv
│   │   └── screenshot/
│   │       └── raw.png
│   │
│   └── clean/
│       ├── files/
│       │   └── concert_tour_clean.xlsx
│       └── screenshot/
│           ├── clean.png
│           ├── clean_1.png
│           └── rank_duplicate.png
│
└── README.md
```

## 📂 Dataset Information
- Source: Kaggle
- Dataset Name: Dirty Dataset for Data Cleaning Practice
- Link: https://www.kaggle.com/datasets/amruthayenikonda/dirty-dataset-to-practice-data-cleaning
- Description: A purposely messy dataset containing concert tour data, designed for practicing data cleaning skills. It includes inconsistencies such as  symbols, missing values, incorrect formats, and duplicate rankings.
- License: CC0: Public Domain

---

## Full Data Analytics Pipeline
---
### Step 1: Bringing Data
⚠️ Issues in Raw Data
- Duplicate value in `Rank` column
- Broken ranking sequence
- Currency symbols ($) and commas in numeric columns
- Footnotes like `[x]`, `[b]`, `[e]`
- Special symbols (†, ‡, *) in text fields
- Inconsistent Year formats (single year vs range)
- Numeric columns stored as text

---

**View Screenshot**

[Raw Dataset](data/raw/screenshot/raw.png)

---

### Step 2: Data Cleaning and Formatting
The following cleaning steps are performed to clean the above raw data set to ensure data accuracy and consistency.

#### 1. Remove Unnecessary Columns
- Peak
- All Time Peak
- Ref

**View Screenshot**

[Removing Unnecessary_Columns](cleaning/screenshot/extra_columns.png)

---

#### 2. Rank Column Fix
- Removed duplicate value (7 → corrected to 8)
- Fixed sequence (1–20 continuous)

**View Screenshot**

[Rank Column Fix_1](cleaning/screenshot/rank_duplicate_1.png)

[Rank Column Fix_2](cleaning/screenshot/rank_duplicate_2.png)

---

#### 3. Actual_Gross Cleaning

Steps performed:

- Removed $ using Find & Replace
- Removed commas ,
- Removed footnotes [b], [e]
- Converted to numeric

**View Screenshot**

[Removing footnotes](cleaning/screenshot/gross_footnotes.png)

[Converting to numeric](cleaning/screenshot/gross_number.png)

---

#### 4. Adjusted_Gross Cleaning

Steps performed:

- Removed $ using Find & Replace
- Removed commas

**View Screenshot**

[Adjusting_Gross](cleaning/screenshot/adjusted_Gross_number.png)

---

#### 5. Tour Title Cleaning

Removed symbols using Find & Replace:

- †, ‡, *
- [4], [a], [21]

**View Screenshot**

[Removing Unwanted Symbols](cleaning/screenshot/tourtitle_symbol.png)

---

#### 6. Years Column Transformation
##### Converted single year to range using formula:
**Formula:**
```excel
= IF(ISNUMBER(FIND("–",H2)),H2,H2&"–"&H2)
````
2012 → 2012–2012

**View Screenshot**

[Single Year to Range](Analysis/screenshot/year_range.png)

##### Created new columns:
- Start_Year USING FORMULA:

**Formula:**
```excel
= LEFT(H2,4)
````

**View Screenshot**

[Start_Year](Analysis/screenshot/start_year.png)

- End_Year USING FORMULA:

**Formula:**
```excel
= IF(ISNUMBER(FIND("–",H2)),RIGHT(H2,4),H2)
````

**View Screenshot**

[End_Year](Analysis/screenshot/end_year_1.png)

- Converted to numeric USING FORMULA:

**Formula:**
```excel
= VALUE(I2)
````

**View Screenshot**

[Converting Start Year to numeric](cleaning/screenshot/start_year_value.png)

**Formula:**
```excel
= VALUE(J2)
````

**View Screenshot**

[Converting End Year to numeric](cleaning/screenshot/end_year_value.png)

---

##### Removed original Years column and additional range column

---


---
## Clean Dataset Columns:
- Rank
- Artist
- Tour_Title
- Start_Year
- End_Year
- Shows
- Actual_Gross
- Adjusted_Gross
- Avg_Gross

**View Screenshot**

[clean Dataset](data/clean/screenshot/clean_1.png)

---

## Step 3. ⚙️ Preparing for Analysis
---
### ➕ Dataset Enhancement by adding Helper Columns
- Tour Duration USING FORMULA:

**Formula:**
```excel
= G2 - F2 + 1
````

**View Screenshot**

[Tour Duration](Analysis/screenshot/tour_duration.png)

- Revenue per Show USING FORMULA:

**Formula:**
```excel
= B2/H4
````

**View Screenshot**

[Revenue/Show](Analysis/screenshot/revenue_per_show.png)

---

### Step 4: Bringing data into a visualization tool
---
#### 1. Top Earning Artists
- Rows → Artist
- Values → Sum of Actual_Gross

👉 Identifies highest revenue-generating artists

---

#### 2. Top Tours
- Rows → Tour_Title
- Values → Actual_Gross

👉 Shows highest grossing tours

---

#### 3. Shows vs Revenue
- Rows → Shows
- Values → Actual_Gross

👉 Analyzes relationship between shows and revenue

---

#### 4. Revenue Over Time
- Rows → Start_Year
- Values → Sum of Actual_Gross

👉 Identifies growth trends

---

#### 5. Average Gross Comparison
- Rows → Artist
- Values → Avg_Gross

👉 Compares earnings per show

---

### Step 5: Visualizing Data by Pivot Charts

Visualized Insights by creating Pivot Charts from above Pivot Tables created

---

#### 💡 Key Insights Generated

- Revenue is concentrated in a small number of top artists — the top 5 account for roughly **85 %** of total revenue in the dataset
- The single highest-grossing tour was "The Eras Tour", generating **$780000000**
- More shows does not reliably mean more revenue — e.g. "The Eras Tour" had fewer shows but higher total revenue than "Living Proof:    The Farewell Tour" which had most shows
- Revenue peaked in 2023 and was lowest in 2006
- "Taylor Swift" was the single highest overall earner  at **$1526075146** in total gross revenue

---

## Step 6: 📈 Dashboard
### 🧾 Layout Structure
#### 🔷 Top Section (KPIs)
- Total Revenue
- Total Shows
- Number of Artists
- Average Revenue per Show
#### 🔷 Middle Section (Charts)
- Top Artists 
- Revenue Trend
#### 🔷 Bottom Section (Charts)
- Top Tours
- Shows vs Revenue 
#### 🔷 Side Panel (Slicers)
- Artist
- Year

---

Dashboard Screenshot:
![Dashboard](dashboard/screenshot/dashboard.png)

---

## 🚀 Conclusion

This project demonstrates strong skills in:
- Data cleaning
- Data transformation
- Excel-based analysis
- Dashboard creation

It highlights how raw, messy data can be turned into valuable, quantified insights through a structured, repeatable process.

---

## 👤 Author

**Yasir Shah**
- GitHub: [@yasirshah-analyst](https://github.com/yasirshah-analyst)
- www.linkedin.com/in/yasir-shah-2364183b3
- shahyasir443@gmail.com

---

