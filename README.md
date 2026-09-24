# COVID-19 India EDA

Exploratory data analysis of India's COVID-19 first wave (Jan to Aug 2020) plus the vaccination rollout from 2021. Mini project for Module 1 of my Data Science & ML course.

## What's in here

- `covid19_india_eda.ipynb` - the full analysis
- `cleaned_covid_india.csv` - cleaned state-wise daily data (the notebook creates this when you run it)

## Data

- State-wise daily cases, recoveries and deaths: [imdevskp/covid-19-india-data](https://github.com/imdevskp/covid-19-india-data) (`complete.csv`, 30 Jan to 6 Aug 2020)
- Vaccinations: [Our World in Data](https://github.com/owid/covid-19-data) India file (Jan 2021 to Aug 2024)

The notebook reads both straight from GitHub, so you don't have to download anything.

## What I did

**Cleaning.** The Death column was stored as text because of one bad value (`0#`). A few states showed up under two or three names (Telangana was spelled three ways, and Chandigarh, J&K and Ladakh had "Union Territory of" duplicates), so I merged them, which took it from 40 names to 35. There were also 4 missing dates and one day where the numbers didn't update, so I filled those by interpolation.

**Analysis.** National totals and daily new cases, a snapshot of every state on the last date, recovery and death rates by state, a state x month pivot of new cases, and the vaccination progress. 16 charts in total.

**Extra stuff I added:**
- compared case growth across the lockdown and unlock phases
- doubling time for India and the top 15 states
- active cases vs each state's own peak, to see which states had actually turned the corner

## Some findings

- About 19.6 lakh cases and 40.7k deaths by 6 Aug 2020, and cases were still rising when the data ends
- Maharashtra had about 24% of all cases. The top 5 states together had 62%
- Delhi recovered almost 90% of its cases. Karnataka was under 50%
- Gujarat (3.8%) and Maharashtra (3.5%) had the highest death rates among the bigger states
- Daily growth fell from about 16% in the first lockdown to under 4% by July, and doubling time went from about 4 days to about 3 weeks, but daily new cases kept going up
- Delhi was the only big state clearly past its peak by August

## How to run

```
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook covid19_india_eda.ipynb
```

Then run all cells. You need an internet connection since the data loads from GitHub.

## Limitations

The case data stops in August 2020 and the source isn't maintained anymore. Reported numbers depend on testing, which was very different across states. I didn't have population data, so I compared states using rates instead of per-capita numbers.
