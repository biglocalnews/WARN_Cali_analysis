## California’s layoffs and closures of 2019 and 2020 by Big Local News

The coronavirus pandemic disrupted the lives and livelihoods of many people in 2020. COVID-19 impacted everything from education, food supply, health care to the job market and housing. In our evictions story, we look at how pressure on renters during the pandemic resulted in evictions and how layoffs contributed to an already unstable housing situation for many.

This repository shares the data about layoffs and closures in california from 2019-2020. Layoffs and closures have always been a consistent presence in the market place. For the purposes of our story, we analyzed 2019s data and compared it to 2020 data, in order to assess the difference in job losses from a non-pandemic year to a pandemic year. 

For the purposes of this story, we've only done specific analyses on counties with high rent burdens and public housing authorities. There are many patterns alive in this data we have yet to explore and we are sharing it with the hopes that other data journalists and news organizations will report similar stories of their own - and share their counties and cities have been impacted by layoffs and clsures.


### Data Gathering and Ordering

This data was used as a section in a larger evictions story written by Big Local News. 

The data was collected from:
- California WARN data: https://edd.ca.gov/Jobs_and_Training/Layoff_Services_WARN.htm
- population data from: https://www.census.gov/data/tables/time-series/demo/popest/2010s-counties-total.html#par_textimage_242301767

### Notebooks

- `1_cali_hist_data.ipynb` walks through the steps taken to combine the data and create the historical california warn layoffs file.
- `2_winnow_counties.ipynb` walks through the steps taken to look into california counties based on high rent payments at the household level. Households that pay more than 50% of their gross income in rent are considered to fall under the category of households with a high rent burden. 
- `3_rent_burden_calc.ipynb` walks through the steps taken to add data detailing median gross rent as a percentage of household income per county, which then gets combined with the public housing authorities table and the high rent burden percentage per county table. 
- `4_cali_warn_ambiguous_cities.ipynb` walks through the steps taken to figure out which cities have the incorrect county listed due to data entry errors. 
- `5_cali_warn_analysis_2019_2020.ipynb` walks through the full analysis of the data and how the figures that ended up in the evictions story were extracted.

### Directories

Data in the `cali_hist_data/` directory is linked to `1_cali_hist_data.ipynb`. 
- Each of the files ending in `.pdf` is the actual downloaded PDF from California's WARN Notices website. 
- Each file ending in `.csv` of the same name is the comma-seperated-values version of those PDF tables. - `cali_warn_hist.csv` is a file of all the years 2014-2019 combined. 
- The California WARN Notices scraper scrapes the website daily and adds the entries from 2020-on to the historical file creating a complete version of the data. This file you can find in `analysis_data/california_warn_raw_recent.csv`.

Data in the `rent_burden_data/` directory is linked to `2_winnow_counties.ipynb` and `3_rent_burden_calc.ipynb`.

- The `ACS_2018_5year_est.csv` file contains information on the number of households that pay 10%, 15%, 20%, etc, up to 50% of their income in rent per county.
- The `ACS_2018_5year_median_gross_rent_percent_of_income.csv` file contains information about median gross rent as a percentage of household income per county.
- The `ACS_2018_5year_rentburden.csv` file contains just information for number of households that pay more than 50% of their income in rent - and a calculation for what % of the households within a specific county fall under that category.
- The `california_warn_raw.csv` file contains the california layoffs data that was most recent when we did the analysis for winnowing the counties and calculating rent high rent burden. This data is technically out of date now and our analysis notebooks use the most recent data we can get. The calculation of rent burden and selection of counties is not impacted the out of date file because layoffs and closures were not a part of high rent burden, and median gross rent as a percentage of income calculations.
- The `Housingauthorities.csv` file contains all of the public housing authorities in California. The file lists the public housing authorities in each county, in addition to other important information such as size, number of units, etc.
- The `rent_burden_households_and_median_gross_rent_percent.csv` file is a combination of the `Housingauthorities.csv`,`ACS_2018_5year_median_gross_rent_percent_of_income.csv` and `ACS_2018_5year_rentburden.csv` files.
- The `truncated_rent_burden_and_median_gross_rent_pct.csv` file is a truncated version of the `rent_burden_households_and_median_gross_rent_percent.csv` file that focuses on the public housing authority names, fips codes and high rent burden percentage. 

Data in the `analysis_data/` directory is linked to `4_cali_warn_ambiguous_cities.ipynb` and `5_cali_warn_analysis_2019_2020.ipynb`.

- The `california_warn_raw_recent.csv` file has the most recent data scraped from California's WARN Layoffs website, combined with the historical data from the `cali_hist_data` directory.
- The `california_warn_raw_2.csv` is the file that we get after we take the recent data file and single out the ambiguous cities (cities where two counties are listed). A little data cleaning in the `County` field does happen, so when this file is exported, it's named version 2 instead of recent.
- The `county_population.csv` file contains census population data for each county.
- The `tobecleaned_california_warn.csv` is the file `5_cali_warn_analysis_2019_2020.ipynb` exports to this directory after `california_warn_raw_2.csv` has been given the correct county names and goes through some data cleaning. At this point in the notebook, this file needs Open Refine to standardize the company names in order to rule out duplicate entries.
- The `cleaned_cali_warn_raw.csv` file is the re-imported version of `tobecleaned_california_warn.csv` after the `Company` column has been processed with data standardization algorithms in open refine. This is the file we will actually run the analysis on. 


