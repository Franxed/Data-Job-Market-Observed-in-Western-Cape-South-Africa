<div align="center">

# 🗂️ Western Cape Data Job Market Analysis
### A real-world end-to-end data analytics portfolio project

![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=flat&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=flat&logo=powerbi&logoColor=black)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow?style=flat)

*Data scraped: 1 June – 13 June 2026 · Location: Western Cape, South Africa*

</div>

---

## 📌 Overview

This project analyses the **data job market in the Western Cape, South Africa**, using 190 real job listings scraped from Indeed and LinkedIn. It demonstrates a complete, professional data analytics workflow — from raw data collection through to cleaning, exploratory analysis, SQL querying, and a Power BI dashboard.

> Built as a portfolio project to showcase practical, end-to-end data analytics skills in the context of the South African job market.

---

## 🗃️ Project Structure

```
📁 Data-Job-Market-Observed-in-Western-Cape-South-Africa
│
├── 📄 wc_data_jobs_scraper.py       ← Custom web scraper (jobspy)
├── 📓 Data_cleaning.ipynb           ← Part 1: Data cleaning & transformation
├── 📓 eda.ipynb                     ← Part 2: Exploratory data analysis
├── 📄 sql_queries.sql               ← Part 3: SQL analysis (coming soon)
├── 📊 dashboard.pbix                ← Part 4: Power BI dashboard (coming soon)
│
├── 📂 data/
│   ├── wc_data_jobs_20260613.csv    ← Raw scraped dataset (289 rows)
│   └── wc_jobs_cleaned.csv          ← Cleaned dataset (190 rows)
```

---

## 🔧 Tools & Technologies

| Category | Tools |
|---|---|
| **Data Collection** | Python, jobspy, requests |
| **Data Cleaning** | Pandas, NumPy, Regex |
| **Analysis & Visualisation** | Matplotlib, Seaborn, Jupyter Notebook |
| **Database** | SQL, SQLite *(coming soon)* |
| **Dashboard** | Power BI *(coming soon)* |
| **Version Control** | Git, GitHub |

---

## 📊 Dataset

| Property | Detail |
|---|---|
| **Sources** | Indeed + LinkedIn (via `jobspy`) |
| **Date scraped** | 13 June 2026 |
| **Raw rows** | 289 listings |
| **Cleaned rows** | 190 unique, relevant listings |
| **Location** | Western Cape, South Africa |
| **Roles searched** | Data Analyst, Data Scientist, Data Engineer, ML Engineer, AI Engineer, BI Analyst, Analytics Engineer, Business Analyst, Data Architect |

---

## 🧹 Part 1 — Data Cleaning [`Data_cleaning.ipynb`]

The raw scraped data required significant transformation before analysis.

| Step | Action |
|---|---|
| 1 | Converted `date_posted` from string to datetime format |
| 2 | Dropped entirely empty salary columns (`min_amount`, `max_amount`, `currency`, `interval`) |
| 3 | Extracted city from inconsistent location strings; grouped Cape Town suburbs under `"Cape Town"` |
| 4 | Engineered a `Level` column (Senior / Mid-Level / Junior) from job title keywords |
| 5 | Standardised `job_type` values — resolved `"parttime, fulltime"` ambiguity |
| 6 | Cleaned job description text by stripping raw markdown characters using Regex |
| 7 | Filtered out non-data role titles (SOC Analyst, DevOps Engineer, etc.) with a two-step include/exclude keyword filter |
| 8 | Renamed all columns to human-readable format |
| 9 | Filled remaining nulls with `"Unknown"` to preserve rows for analysis |

**Result:** 289 raw rows → 190 clean, analysis-ready rows

---

## 🔍 Part 2 — Exploratory Data Analysis [`eda.ipynb`]

Six questions were explored:

### 1. 🏆 Role Demand — *What types of data roles are most common?*
- **Analysts dominate** the market by a significant margin
- Reflects a WC market that values interpreting data over building infrastructure
- Engineers are a strong second — pipeline and data engineering roles are growing

### 2. 👔 Seniority — *What experience level does the market expect?*
| Level | Count | Share |
|---|---|---|
| Mid-Level | 135 | 71% |
| Senior | 48 | 25% |
| Junior | 7 | 4% |
> The WC market is tough for entry-level candidates — only 4% of listings are junior roles.

### 3. 🏢 Top Hiring Companies — *Who is actively recruiting?*
- **Recruitment agencies dominate** listings (ExecutivePlacements.com, Network Recruitment, Communicate Recruitment)
- Top **direct employers**: Capitec, Sanlam, Auto Trader South Africa
- Agency dominance means the actual employer market is more concentrated than listing counts suggest

### 4. 💻 Remote Work — *How flexible is the market?*
| Arrangement | Count | Share |
|---|---|---|
| On-site | 179 | 94.2% |
| Remote | 11 | 5.8% |
> Remote opportunities are rare — physical location in Cape Town is a real barrier to entry.

### 5. 📍 Location — *Where are the jobs?*
| City | Listings | Share |
|---|---|---|
| Cape Town | 174 | 91.6% |
| Stellenbosch | 14 | 7.4% |
| Paarl | 1 | 0.5% |
| Darling | 1 | 0.5% |
> Cape Town is the undisputed hub. Stellenbosch activity is driven largely by Capitec's HQ.

### 6. 🛠️ In-Demand Skills — *What tools do employers ask for?*

Extracted by scanning all job descriptions for keyword mentions:

| Rank | Skill | Mentions |
|---|---|---|
| 1 | Excel | 45 |
| 2 | SQL | 29 |
| 3 | Git | 21 |
| 4 | Python | 17 |
| 5 | AWS | 15 |
| 5 | Azure | 15 |
| 7 | Power BI | 9 |
| 8 | Tableau | 6 |
| 8 | Machine Learning | 6 |
| 10 | Spark | 4 |

> Excel leads due to its prevalence in financial services roles. SQL and Python are the core technical requirements. Cloud tools (AWS, Azure) are growing but not yet universal at this market level.

---

## 🔑 Key Findings Summary

| Finding | Detail |
|---|---|
| Most in-demand role | Analyst |
| Dominant seniority | Mid-Level (71%) |
| Junior opportunities | Scarce — only 7 listings (4%) |
| Top direct employers | Capitec, Sanlam |
| Remote availability | 11 listings (5.8%) |
| Geographic hub | Cape Town — 91% of all listings |
| Most mentioned skill | Excel (45 mentions) |
| Core technical skills | SQL (29) and Python (17) |

---

## ▶️ How to Run the Scraper

```bash
# 1. Install dependencies
pip install python-jobspy pandas

# 2. Run the scraper
python wc_data_jobs_scraper.py
```

The scraper targets Indeed and LinkedIn, applies randomised delays between requests to avoid rate limiting, deduplicates across sources and search terms, and saves a timestamped CSV to the current directory.

> ⚠️ **If you receive 429 errors:** wait 15 minutes and reduce `RESULTS_PER_ROLE` to `20` in the configuration section at the top of the script.

---

## 🗺️ Roadmap

- [x] Data collection — custom web scraper
- [x] Data cleaning & transformation
- [x] Exploratory data analysis & visualisation
- [ ] SQL analysis — querying the dataset with SQLite
- [ ] Power BI dashboard — interactive visual summary

---

## 👤 About

Built by **Franx** as part of a self-directed data analytics learning path, working toward entry-level data analyst roles in the Western Cape, South Africa.

[![GitHub](https://img.shields.io/badge/GitHub-Franxed-181717?style=flat&logo=github)](https://github.com/Franxed)
[![Project](https://img.shields.io/badge/Project-Repo-blue?style=flat&logo=github)](https://github.com/Franxed/Data-Job-Market-Observed-in-Western-Cape-South-Africa)
