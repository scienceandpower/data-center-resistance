# Data Center Siting, Resistance, and Cancellation

This analysis looks at the characteristics of neighborhoods across three stages of the recent data center buildout and resistance movement:

**Siting:** What kinds of neighborhoods are being targeted for data centers?

**Fighting:** What kinds of neighborhoods are pushing back against data centers?

**Spiking:** What kinds of neighborhoods are effectively disrupting proposed data centers?

## Key findings

**Siting:** Compared to currently operating data centers, recently proposed ones target areas with lower median incomes, lower educational attainment, and higher homeownership rates — areas where residents can neither easily get the jobs these facilities create nor easily move away.

**Fighting:** Neighborhoods with the *lowest* incomes and *lowest* rates of college graduation were most likely to push back. Resistance was markedly lower in high-income, highly-educated neighborhoods — the opposite of the NIMBY stereotype.

**Spiking:** Cancellation rates are highest in lower-income areas, a fact fully explained by their higher rates of pushback. The odds of cancellation are roughly six times higher in neighborhoods that fight than in neighborhoods that don't. Beyond pushback, nothing about a neighborhood's demographics predicts cancellation.

## Repository contents

| File | Description |
|---|---|
| `census_etl.Rmd` | Pulls tract-level ACS variables for data center locations; run this first |
| `data_center_resistance_analysis.Rmd` | Main analysis; run after the ETL |
| `data/Data_Centers_Database - FracTracker Data Centers.csv` | Source data, downloaded from FracTracker |
| `data/datacenter_census_etl.csv` | Output of `census_etl.Rmd` — one row per data center with ACS variables |
| `data/nat_benchmarks.csv` | Output of `census_etl.Rmd` — national ACS benchmarks (income, college rate, homeownership) |
| `data/urban_rural_tract_etl.csv` | Pre-built file: share of each tract's area within a 2020 Census urban boundary |

## How to run

**Prerequisites:**

- Necessary: R with the following packages: `tidyverse`, `tidycensus`, `tigris`, `sf`, `scales`, `knitr`, `kableExtra`, `broom`
- Optional: If redownloading ACS data, you will need a Census API key registered at [api.census.gov](https://api.census.gov/data/key_signup.html), set via `tidycensus::census_api_key()`

**Order of execution:**

1. Optional: Knit `census_etl.Rmd` — regenerates `data/datacenter_census_etl.csv`. A copy of this .csv is already in the repo.
2. Necessary: Knit `data_center_resistance_analysis.Rmd` — produces the full analysis

Note: `census_etl.Rmd` makes live API calls to the Census Bureau and may take several minutes to run. Results are cached locally after the first run.

## Data sources

- **FracTracker Data Centers Database** — [arcgis.com](https://www.arcgis.com/apps/instant/sidebar/index.html?appid=fdb7678fb2e345eb8b0a3a49971240c4)
- **ACS 5-year 2024 (2020–2024)** — U.S. Census Bureau, via the `tidycensus` R package
- **2020 Census urban area definitions** — U.S. Census Bureau, used to classify tract urbanicity

## Notes

Methods, results, and terminology are explained further in the .Rmd files and the HTMLs they produce

## Code author

Geoffrey S. Holtzman, PhD ([Science & Power](https://scienceandpower.substack.com))
