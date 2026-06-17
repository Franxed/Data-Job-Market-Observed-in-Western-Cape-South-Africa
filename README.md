Western Cape Data Job Market Analysis

A real-world data analytics portfolio project (data scraped 1 June to 13 June 2026)


Project Overview

This project analyses the data job market in the Western Cape, South Africa, using real job listings scraped from Indeed and LinkedIn. It covers the full data analytics workflow from raw data collection through to cleaning, exploratory analysis and a Power BI dashboard.

The project was built as a portfolio piece to demonstrate practical, end-to-end data analytics skills in the context of the South African job market.


Project Structure

├── wc_data_jobs_scraper.py       # Custom web scraper (jobspy)
├── Data_cleaning.ipynb           # Part 1: Data cleaning & transformation
├── eda.ipynb                     # Part 2: Exploratory data analysis
├── sql_queries.sql               # Part 3: SQL analysis (coming soon)
├── dashboard.pbix                # Part 4: Power BI dashboard (coming soon)
├── wc_data_jobs_20260613.csv     # Raw scraped dataset (289 rows)
└── wc_jobs_cleaned.csv           # Cleaned dataset (190 rows)


Dataset


Source: Indeed and LinkedIn (via jobspy)
Scraped: 13 June 2026
Raw rows: 289 listings across 9 search roles
Cleaned rows: 190 unique, relevant listings
Roles searched: Data Analyst, Data Scientist, Data Engineer, Machine Learning Engineer, AI Engineer, Business Intelligence Analyst, Analytics Engineer, Business Analyst, Data Architect
Location: Western Cape, South Africa



Part 1 - Data Cleaning (Data_cleaning.ipynb)

The raw scraped data required significant cleaning before analysis. Steps performed:


Datetime conversion: Converted date_posted from string to proper date format
Dropped empty columns: Salary columns (min_amount, max_amount, currency, interval) were entirely null across all listings. Removed to reduce noise
Location standardisation: Extracted city from inconsistent location strings, consolidated Cape Town suburbs (Bellville, Milnerton, Century City, etc.) into "Cape Town"
Seniority extraction: Engineered a Level column (Senior / Mid-Level / Junior) by scanning job titles for seniority keywords
Job type standardisation: Resolved inconsistent values ("parttime, fulltime" → "Full-Time") and applied consistent formatting
Description cleaning: Removed raw markdown formatting characters (**, ###, \n, ---) using Python Regex
Title filtering: Removed non-data roles (SOC Analyst, DevOps Engineer, etc.) that slipped through the scraper using a two-step include/exclude keyword filter
Column renaming: Standardised all column names to human-readable format
Null handling: Filled remaining nulls with "Unknown" to preserve rows for analysis



Part 2 - Exploratory Data Analysis (eda.ipynb)

Six analysis questions were explored:

1. What seniority level does the market demand?


135 Mid-Level (71%), 48 Senior (25%), 7 Junior (4%)
The WC data market is overwhelmingly mid-level. Entry-level roles are scarce


2. What types of data roles are most in demand?


Analysts dominate, followed by Engineers
Reflects a market that prioritises interpreting data over building infrastructure


3. Which companies are hiring the most?


Top listings come from recruitment agencies (ExecutivePlacements.com, Network Recruitment, Communicate Recruitment)
Top direct employers: Capitec, Sanlam, Auto Trader South Africa
Agencies dominate the listing count, meaning actual employer concentration is higher than it appears


4. How available is remote work?


Only 11 out of 190 listings (5.8%) are remote
The WC data market is largely on-site.


5. Where are jobs located?


Cape Town: 174 listings (91%) of all roles
Stellenbosch: 14 listings are driven largely by Capitec's headquarters
Paarl and Darling: minimal presence


6. What skills do employers ask for?


SQL and Python are the most frequently mentioned skills by a clear margin
Power BI and Excel rank highly, reflecting the corporate and financial services of WC employers
Cloud tools (AWS, Azure) and pipeline tools (dbt, Airflow) appear less frequently at this market level



Key Findings

FindingDetailMost in-demand roleAnalystDominant seniorityMid-Level (71%)Junior opportunitiesScarce — only 7 listings (4%)Top direct employersCapitec, SanlamRemote availability11 listings (5.8%)Geographic hubCape Town — 91% of all listingsMost mentioned skillSQLSecond most mentionedPython


How to Run the Scraper

bash# Install dependencies
pip install python-jobspy pandas

# Run
python wc_data_jobs_scraper.py

The scraper targets Indeed and LinkedIn, applies polite delays between requests, deduplicates across sources and search terms and saves a timestamped CSV to the current directory.


Note: If you receive 429 errors, wait 15 minutes and reduce RESULTS_PER_ROLE to 20 in the config section of the script.







About

Built by Franx as part of a self-directed data analytics learning path, working toward entry-level data analyst roles in the Western Cape.


GitHub: @Franxed
Project repo: Data-Job-Market-Observed-in-Western-Cape-South-Africa
