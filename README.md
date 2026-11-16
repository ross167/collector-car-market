# Is the collector car market getting younger?

A data analysis of the key collector car auctions in the US and Europe, comparing the most valuable cars sold in the last 12 months with the same sales three years earlier.

![Share of top-lot value by era](images/era_share.png)

## Key findings

- **The top lot is 27 years younger.** The median model year of the 67 most valuable lots moved from **1967** (2023 editions) to **1994** (2026 editions). The 95% bootstrap interval for the shift is 19 to 36 years.
- **The money has moved to younger cars.** Cars built since 1980 took **27%** of top-lot value three years ago and **62%** now. Cars built before 1970 fell from 68% to 36%.
- **The difference is significant.** Mann-Whitney U on model year: p < 0.001. Chi-square of era against edition: p = 0.002, Cramér's V = 0.36.
- **The high end grew fastest.** Monterey went from $400m to $756m, Paris rose 49% and Amelia 43%. Arizona and RM Sotheby's London were flat.

- **The cars have moved faster than the collectors.** Hagerty's data shows younger generations asking for more quotes and wanting collector cars more, but boomers still hold 52% of insured cars and their share of new applications rose in 2025. The market looks like it is being handed on, not replaced.

![Sale totals](images/sale_totals.png)

## Data

| Sale | Last 12 months | Three years earlier | Lots used |
|---|---|---|---|
| Monterey Car Week (five houses) | August 2026 | August 2023 | Top 30 |
| Amelia Island | March 2026 | March 2023 | Top 10 |
| RM Sotheby's Arizona | January 2026 | January 2023 | Cars over about $1m |
| RM Sotheby's Paris | January 2026 | February 2023 | Top 15 |

Collected by hand from public results (collector generations from Hagerty's published data): auction-house press releases, Hagerty's auction reports, classic-car-auctions.info and classic.com. Prices include buyer's premium.

## Notebooks

| Notebook | What it does |
|---|---|
| [01_data_collection](notebooks/01_data_collection.ipynb) | Sources, loading and checking the raw data |
| [02_cleaning_and_features](notebooks/02_cleaning_and_features.ipynb) | A like-for-like sample (67 lots each edition), eras and price features |
| [03_eda](notebooks/03_eda.ipynb) | Sale totals, value by era, model year shift, year against price |
| [04_hypothesis_testing](notebooks/04_hypothesis_testing.ipynb) | Mann-Whitney U, chi-square with Cramér's V, bootstrap intervals |
| [05_collector_demographics](notebooks/05_collector_demographics.ipynb) | Context: collectors by generation, and whose teenage years the top lots come from |

![Model year shift](images/model_year_shift.png)

![Top lots by model year and price](images/year_vs_price.png)

## Who are the collectors?

No auction house publishes buyer ages, so notebook 05 puts the published figures (Hagerty insurance and survey data) beside our results. It also gives each top lot the generation that was 15 when the car was new: nearly two-thirds of top-lot value now comes from the teenage years of Gen X and younger, up from about a quarter in 2023.

![Collectors by generation](images/collector_generations.png)

![Top-lot value by generation](images/poster_generation.png)

## Limitations

- Top lots only, not every car sold, so it says nothing about the mid-market.
- Hand-collected public data; sources count slightly differently.
- Four sales and two editions cannot separate a lasting trend from the mix of cars consigned in a given year.
- Paris runs against the trend on value share: its 2023 sale was led by a new $10.7m Bugatti.
- Collector ages come from Hagerty's published figures, which cover its own customers and mostly the US.
- Goodwood is not compared (no comparable 2026 results published), nor is Broad Arrow Zürich (first held in 2025).

## Running it

```
pip install -r requirements.txt
cd notebooks
jupyter notebook
```

Run the notebooks in order: 02 writes the processed files that 03 and 04 read.

## Tools

Python, pandas, NumPy, SciPy, Matplotlib, seaborn, Jupyter.

## Repository structure

```
data/
  raw/          top_lots.csv, sale_totals.csv, collector_generations.csv
  processed/    cleaned outputs from notebook 02
images/         figures saved by the notebooks
notebooks/      01 to 05
```
