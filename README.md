## California’s layoffs and closures of 2019 and 2020.

### Data Gathering and Ordering

This data was used as a section in a larger evictions story written by Big Local News. 

The data was collected from:
- California WARN data: https://edd.ca.gov/Jobs_and_Training/Layoff_Services_WARN.htm
- population data from: https://www.census.gov/data/tables/time-series/demo/popest/2010s-counties-total.html#par_textimage_242301767

`1_cali_hist_data.ipynb` walks through the steps taken to combine the data and create the historical file.
`2_winnow_counties.ipynb` walks through the steps taken to look into california counties based on high rent payments at the household level.
`3_rent_burden_calc.ipynb` walks through the steps taken to figure out which counties with high rent burdens also have public housing authorities. 
`4_cali_warn_ambiguous_cities.ipynb` walks through the steps taken to figure out which cities have the incorrect county listed due to data entry errors. 
`5_cali_warn_analysis_2019_2020.ipynb` walks through the full analysis of the data and how the figures that ended up in the evictions story were extracted.

### Background on Analysis

A large portion of our story focuses on evictions as they relate to Public Housing Authorities.

When initially deciding which counties to focus on, we took the public housing spreadsheet which identifies all public housing authorities in California, `rent_burden_data/Housingauthorities.csv`. We then took rent burden information to calculate which counties had the highest rent burdens & had public housing authorities in the county. 

From there, we got a list of high rent burden counties which we focused on for our analysis. 

Notebook ‘finding_ambiguous_counties.ipynb’ helps us do some preliminary data cleaning to identify cities that have been assigned to the wrong county & correct the data. 
Notebook ‘hard_hit_draft3.ipynb’ has the full analysis of the data.

cali_hist_data.ipynb - historical data grabbed from the layoffs site (2014-2020) - re compare this and check scraper to see if all of the data is still there, if not, fix so that we can have all the same data


winnow_counties.ipynb - Takes ACS 2018 5 year estimates information on households paying a % of their income in rent. We take the # of households paying more than 50% rent to calculate counties with the highest rent burdens. (‘ACS_2018_5year_est.csv’) is the file it takes in, (‘ACS_2018_5year_rentburden.csv’) is the file it produces.

rent_burden_calc.ipynb -  This notebook adds (‘ACS_2018_5year_median_gross_rent_percent_of_income.csv’) and (‘Housingauthorities.csv’)  to look at median gross rent as a percentage of household income for each county. Then it is combined with the  (‘ACS_2018_5year_rentburden.csv’) file from the winnow_counties.ipynb to identify which counties have a high rent burden that overlap with counties with public housing authorities. This results in the csv (‘rent_burden_households_and_median_gross_rent_percent.csv’) which helped us decide which counties to look into based on high rent burden and public housing authorities.

