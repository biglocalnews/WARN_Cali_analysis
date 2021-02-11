## California’s layoffs and closures of 2019 and 2020 by Big Local News

The coronavirus pandemic disrupted the lives and livelihoods of many people in 2020. COVID-19 impacted everything from education, food supply, healthcare to the job market and housing. In our story, we look at how pressure on renters during the pandemic resulted in a frenzy of concern about homelessness and the disproportionate effect on vulnerable populations. We also look at how layoffs contributed to an already unstable housing situation for many.

This repository shares the data about layoffs and closures in California from 2019-2020. Layoffs and closures have always been a consistent presence in the market place. For the purposes of our story, we analyzed the 2019 data and compared it to 2020 data to assess the difference in job losses from a non-pandemic year to a pandemic year. 

In our story, we've focused on a few counties with high rent burdens, where a significant percentage of households pay more than 50% of their income in rent. We also looked into some metropolitan areas that may not have the highest rent burdens, but do have high population density. There are many patterns present in this data we have yet to explore and we are sharing it with the hopes that other data journalists and news organizations will report similar stories of their own - and share their how counties and cities have been impacted by layoffs and closures due to the coronavirus pandemic.


This data was used as a section in a larger evictions story written by Big Local News. 

The data was collected from:
- [California WARN data](https://edd.ca.gov/Jobs_and_Training/Layoff_Services_WARN.htm)
- [population data from](https://www.census.gov/data/tables/time-series/demo/popest/2010s-counties-total.html#par_textimage_242301767)
- [gross rent as a percentage of household income](https://data.census.gov/cedsci/table?q=rent%20as%20percentage%20of%20income&g=0400000US06.050000&tid=ACSDT5Y2019.B25070&tp=true&hidePreview=true)

## Set up

To use the code in this project, install the [pandas](https://pypi.org/project/pandas/) and [jupyter/jupyter lab](https://pypi.org/project/jupyterlab/) libraries.

```
pip install jupyterlab pandas

```

## Usage

[processed_data.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/processed_data.ipynb) and [rent_burden_calculation.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/rent_burden_calculation.ipynb) can be run simultaneously. The `processed` directory holds all WARN layoff records that were downloaded from the Employment Development Department. [processed_data.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/processed_data.ipynb) creates a single file of all those records and exports it back to the `processed` directory.

[rent_burden_calculation.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/rent_burden_calculation.ipynb) takes ACS rent as a % of income data and the list of public housing authorities in California. With these two datasets, the rent burden in each county is calculated and merged with he public housing data, creating a table that shows the rent burden for the counties of each housing authority. This file is exported to the `rent_burden` directory as a full version with all of the columns and a truncated version with only the necessary columns.

Run the following notebooks in order:

1. [data_cleaning.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/data_cleaning.ipynb)
2. [open_refine_dedupe.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/open_refine_dedupe.ipynb)
3. [layoffs_analysis.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/layoffs_analysis.ipynb)

[data_cleaning.ipynb](https://github.com/biglocalnews/WARN_Cali_analysis/blob/master/notebooks/data_cleaning.ipynb) cleans the data.








 


