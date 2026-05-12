# Global Inflation & Food Expenditure Explorer - Shiny Dashboard

![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white) ![Shiny](https://img.shields.io/badge/Shiny-0B5FFF?style=for-the-badge&logo=rstudio&logoColor=white) ![Leaflet](https://img.shields.io/badge/Leaflet-199900?style=for-the-badge&logo=leaflet&logoColor=white) ![OWID](https://img.shields.io/badge/Our%20World%20in%20Data-002147?style=for-the-badge&logo=databricks&logoColor=white)

An interactive Shiny dashboard for Data Visualisation Assignment 3. The app explores how annual inflation and household food expenditure share vary across countries and over time using public data from Our World in Data.


## Table of Contents
- [Problem](#problem)
- [Dataset](#dataset)
- [App Features](#app-features)
- [Reproducible Pipeline](#reproducible-pipeline)
- [Project Structure](#project-structure)
- [Run Locally](#run-locally)
- [Deployment](#deployment)
- [Live Demo](#live-demo)
- [Tech Stack](#tech-stack)
- [Data Source](#data-source)
- [Author](#author)


## Problem

Understanding inflation and household food expenditure patterns helps compare cost-of-living pressures across countries and time. This dashboard enables geographic and temporal exploration to support data-driven insights.


## Dataset

- **Sources:** Our World in Data (OWID)
- **Metrics:** Annual inflation (derived from CPI) and food expenditure share
- **Grain:** Country-year


## App Features

- Interactive world map for inflation (%) and food expenditure share (% of total consumer expenditure)
- Year slider to compare global patterns over time
- Multi-country trend analysis with side-by-side facets
- Country profile with latest values and historical averages
- Summary statistics for selected countries and year ranges


## Reproducible Pipeline

The preprocessing workflow in `preprocess.Rmd`:

1. Loads CPI and food-share datasets
2. Computes annual inflation from CPI by country
3. Joins inflation and food-share by country-year
4. Converts country names to ISO3 codes
5. Downloads and simplifies world boundaries
6. Saves analysis-ready objects as `data_prepped.rds` and `world_simp.rds`


## Project Structure

```
Assignment 3/
├── preprocess.Rmd
├── Shinny App/
│   └── app.R
├── consumer-price-index.csv
├── share-of-consumer-expenditure-spent-on-food.csv
├── data_prepped.rds
├── world_simp.rds
├── Deploy Script.R
└── README.md
```

Note: the folder is currently named `Shinny App` in this repository.


## Run Locally

1. Open `Assignment 3.Rproj` in RStudio (or open the folder in VS Code with R support).
2. Install required packages:

```r
install.packages(c(
  "shiny", "tidyverse", "sf", "leaflet", "countrycode", "bslib", "viridis",
  "rnaturalearth", "rnaturalearthdata", "rmapshaper"
))
```

3. (Optional) Rebuild processed data from raw CSV files by running `preprocess.Rmd`.
4. Run the app:

```r
shiny::runApp("Shinny App")
```


## Deployment

This project uses `rsconnect` to deploy on shinyapps.io.

- App directory: `Shinny App`
- Existing deployed app name: `Assignment-3`

Before deploying from your own account, set your own credentials in R and deploy:

```r
library(rsconnect)

rsconnect::setAccountInfo(
  name = "<your-account>",
  token = "<your-token>",
  secret = "<your-secret>"
)

rsconnect::deployApp(appDir = "Shinny App", appName = "Assignment-3")
```


## Live Demo

- Main app: https://s4083242.shinyapps.io/Assignment-3/


## Tech Stack

- R
- Shiny
- tidyverse
- sf
- leaflet
- countrycode
- bslib
- viridis
- rnaturalearth
- rnaturalearthdata
- rmapshaper


## Data Source

- Consumer Price Index (Our World in Data):
  https://ourworldindata.org/grapher/consumer-price-index
- Food expenditure share (Our World in Data):
  https://ourworldindata.org/grapher/share-of-consumer-expenditure-spent-on-food
