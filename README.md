# Global Inflation & Food Expenditure Explorer

An interactive Shiny dashboard developed for Data Visualisation Assignment 3.

The app explores how annual inflation and household food expenditure share vary across countries and over time, using public data from Our World in Data.

## Live Demo

- Main app: https://s4083242.shinyapps.io/Assignment-3/

## Features

- Interactive world map for:
  - Annual inflation (%)
  - Food expenditure share (% of total consumer expenditure)
- Year slider to compare global patterns over time
- Multi-country trend analysis with side-by-side metric facets
- Country profile view with latest values and historical averages
- Summary statistics for selected countries and year ranges

## Data Sources

- Consumer Price Index (Our World in Data):
  https://ourworldindata.org/grapher/consumer-price-index
- Food expenditure share (Our World in Data):
  https://ourworldindata.org/grapher/share-of-consumer-expenditure-spent-on-food

## Project Structure

- `preprocess.Rmd`: cleans and joins raw datasets, creates `.rds` outputs
- `Shinny App/app.R`: main Shiny application
- `consumer-price-index.csv`: raw CPI data
- `share-of-consumer-expenditure-spent-on-food.csv`: raw food-share data
- `data_prepped.rds`: processed country-year dataset
- `world_simp.rds`: simplified world geometry for mapping
- `Deploy Script.R`: deployment script for shinyapps.io

Note: the folder is currently named `Shinny App` in this repository.

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

## Run Locally

1. Clone this repository.
2. Open `Assignment 3.Rproj` in RStudio (or open the folder in VS Code with R support).
3. Install required packages:

```r
install.packages(c(
  "shiny", "tidyverse", "sf", "leaflet", "countrycode", "bslib", "viridis",
  "rnaturalearth", "rnaturalearthdata", "rmapshaper"
))
```

4. (Optional) Rebuild processed data from raw CSV files by running `preprocess.Rmd`.
5. Run the app:

```r
shiny::runApp("Shinny App")
```

## Reproducible Data Pipeline

The preprocessing workflow in `preprocess.Rmd`:

1. Loads CPI and food-share datasets.
2. Computes annual inflation from CPI by country.
3. Joins inflation and food-share by country-year.
4. Converts country names to ISO3 codes.
5. Downloads and simplifies world boundaries.
6. Saves analysis-ready objects as `data_prepped.rds` and `world_simp.rds`.

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

## Author

- RMIT Data Visualisation Assignment 3 submission
- Student account seen in deployment metadata: `s4083242`
