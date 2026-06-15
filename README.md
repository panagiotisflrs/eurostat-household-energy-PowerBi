# European Household Energy Transition Analysis (2013–2024) with Power BI

## Overview

This project analyzes household energy consumption across European countries from 2013 to 2024 using Power BI.  
The goal is to identify trends in fuel type usage, track the shift toward renewable energy sources, and surface meaningful patterns across countries through interactive visualizations.

The dataset contains information about:
- European country-level household energy consumption
- 10 fuel types (natural gas, electricity, renewables/biomass, coal, heat pumps, and more)
- Annual data from 2013 to 2024
- Consumption measured in Kilotonnes of Oil Equivalent (KTOE)

---

## Dataset

Dataset used: `hh_energy_fuel.csv`  
Source: Eurostat — Final Consumption, Other Sectors, Households (FC_OTH_HH_E)

The dataset was pre-processed using MySQL before being imported into Power BI:
- Redundant columns removed (freq, nrg_bal, unit — constant across all rows)
- Empty strings converted to NULL
- SIEC energy product codes replaced with readable fuel names
- Wide format unpivoted to long format for time-series analysis
- Aggregated exports created for clustering, CAGR, and crossover analysis

---

## Objectives

This project aims to:
- Visualize total household energy consumption trends across Europe
- Compare renewable vs non-renewable consumption by country
- Track each country's renewable energy share over time
- Identify dominant fuel types per country using clustering
- Detect the fastest growing and declining fuel types using CAGR
- Find the crossover point where renewables/biomass exceeded natural gas per country

---

## Power BI Concepts Used

The project demonstrates the use of:

- Filled Map visuals
- Treemap, Line Chart, Bar Chart, and Matrix visuals
- DAX measures for Renewable Share %
- Conditional formatting via Legend fields
- Edit Interactions for independent side-by-side country comparison
- Slicers (dropdown and list) for dynamic filtering
- KPI cards for headline metrics
- Cross-page filter isolation

---

## Report Pages

### 1. Total Energy Consumption
Overview of total household energy consumption across all countries and fuel types from 2013 to 2024. Includes a time-series line chart and a ranked area chart by fuel type.

### 2. Renewable vs Non-Renewable
Treemap showing each fuel type's share of total consumption, alongside a horizontal bar chart comparing renewable vs non-renewable consumption by country. Filterable by year and country.

### 3. Country Comparison
Side-by-side comparison of two independently selected countries. Each side has its own country slicer, renewable share % line chart, and fuel consumption breakdown table — implemented using Edit Interactions so the two sides do not affect each other.

### 4. Energy Profile by Country (2024)
Filled map where each country is colored by its dominant fuel type in 2024 (gas-heavy, electric-heavy, renewables-heavy, etc.), with a supporting cluster table showing the dominant fuel and max consumption value per country.

### 5. CAGR Analysis
Bar chart identifying the top 5 fastest growing and top 5 fastest declining fuel-country combinations by Compound Annual Growth Rate (2013–2024), color coded green and red. Supported by a detail table.

### 6. Renewables Crossover
Map showing which countries crossed over (renewables/biomass exceeded natural gas) and which never did, with KPI cards (26 crossed, 12 never crossed), a crossover year distribution bar chart, and a country-level table.

> Crossover defined as the first year renewables/biomass consumption exceeded natural gas consumption.

---

## Key Findings

- Natural gas and electricity dominate European household energy consumption, accounting for over 55% of total KTOE across the period.
- 26 out of 38 countries crossed over to renewables before or during 2013, reflecting longstanding biomass traditions in Eastern and Northern Europe.
- Heat pumps showed the fastest growth rates (CAGR up to 0.27), while coal and other petroleum products declined the fastest.
- Germany, France, and Italy are the largest consumers in absolute terms, but smaller countries like Austria and Latvia lead in renewables share.
- Ireland stands out as the only Western European country classified as oil-heavy in 2024, driven by high reliance on other petroleum products.
- Renewable share across all countries grew from approximately 19.5% in 2013 to 28% by 2024, with a notable dip around 2016–2018.

---

## Project Structure

```text
eu-household-energy-powerbi/
│
├── README.md
├── dataset/
│   └── hh_energy_fuel.csv
├── exports/
│   ├── unpivote.csv
│   ├── cluster.csv
│   ├── crossover_year.csv
│   └── CAGR.csv
├── screenshots/
│   ├── 01_total_energy_consumption.png
│   ├── 02_renewable_vs_nonrenewable.png
│   ├── 03_country_comparison.png
│   ├── 04_energy_profile_by_country.png
│   ├── 05_cagr_analysis.png
│   └── 06_renewables_crossover.png
└── eu_household_energy.pbix
```

---

## Tools Used

- MySQL (data cleaning and pre-processing)
- Power BI Desktop (data modeling and visualization)
- GitHub

---

## Related Projects

- [European Household Energy Consumption Analysis with MySQL](https://github.com/panagiotisflrs/eurostat-household-energy.git)
