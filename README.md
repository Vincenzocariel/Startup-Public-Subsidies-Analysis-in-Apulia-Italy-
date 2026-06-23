# Startup-Public-Subsidies-Analysis-in-Apulia-Italy-
This project analyzes the relationship between public subsidies and the financial characteristics of innovative startups located in Apulia (Italy).

The objective is to identify which startups received public subsidies, compare them with startups that did not receive any support, and evaluate whether subsidized firms show different economic and financial patterns.

The project was developed as part of an academic research thesis using Python, Pandas, and financial data extracted from AIDA database.

Project Objective

The analysis focuses on three main research questions:

* Which innovative startups in Apulia received public subsidies?
* How are subsidies distributed across firms in terms of size and concentration?
* Do subsidized startups show different financial characteristics compared to non-subsidized startups?

The final goal is to compare subsidized and non-subsidized firms and investigate potential differences in performance indicators.


Dataset Sources

1. RNA – Registro Nazionale Aiuti (Italian Public Subsidies Database)

Contains information about public subsidies granted to firms:

* National company identifier
* Subsidy amount
* Date of concession
* Subsidy measure/program

More than 200 CSV files were collected and merged.


2. Startup Dataset

Custom dataset containing innovative startups located in Apulia region.

Main variables:

* Company name
* Fiscal code
* Province
* Municipality
* Registration date

Total startups analyzed:

* 153 startups



3. AIDA Financial Database

Financial statement information for each startup.

Main variables used:

* Total Assets
* EBITDA
* Revenues
* Number of Employees
* Legal Form
* Province



Methodology

The analysis pipeline follows these steps.

Step 1 — Import and Merge Subsidy Files

All subsidy CSV files are automatically imported and concatenated.

csv_files = sorted(SUBSIDIES_FOLDER.glob("*.csv"))
merge = pd.concat(files, ignore_index=True)



Step 2 — Data Cleaning

Company identifiers were standardized to avoid merge errors.

Cleaning operations:

* Remove spaces
* Convert to uppercase
* Remove formatting inconsistencies
* Handle missing values

clean_company_id()
clean_euro_amount()



Step 3 — Subsidy Filtering

Only subsidies satisfying the project criteria were retained.

Filters applied:

* Subsidies above €1000
* Specific concession date threshold
* Removal of duplicates



Step 4 — Subsidy Classification

Subsidies were divided into categories based on amount.

Categories:

* Small subsidies
* Medium subsidies
* Large subsidies
* Very large subsidies



Step 5 — Aggregation by Firm

Each company was aggregated to compute total subsidies received.

Output:

79 startups received subsidies



Step 6 — Anti Join Analysis

An anti-join operation was performed to identify startups that did not receive subsidies.

Logic:

anti_join = startups.merge(
    subsidies,
    how="left",
    indicator=True
)

Results:

79 subsidized startups
74 non-subsidized startups



Step 7 — Merge with AIDA Financial Data

All startups were matched with financial statement information using tax code.

Matching variable:

Tax code number



Step 8 — Comparative Analysis

A final dataset was created to compare:

Subsidized Startups

versus

Non-Subsidized Startups

Main indicators analyzed:

* Average Total Assets
* Average EBITDA
* Average Revenues
* Number of Employees



Main Analysis Performed

The project includes:

Descriptive Statistics

Comparison of average financial indicators across groups.

Distribution Analysis

Subsidy concentration by amount class.

Comparative Graphs

Visual comparison between:

* Subsidized firms
* Non-subsidized firms

Example:

* Mean Total Assets comparison

Final sample:

153 startups analyzed
79 subsidized startups
74 non-subsidized startups

The project investigates whether public subsidies are associated with stronger financial characteristics among innovative startups.

Author

Vincenzo Cariello

Piccola critica: non caricare su GitHub file chiamati merge con duplicati.csv o codice_finale(5).pdf. Sembra repo disordinata da lavoro in corso. Dai nomi puliti, altrimenti abbassi molto la percezione del progetto.
