## cali_WARN compares California’s layoffs and closures of 2019 and 2020. 

This data was used as a section in a larger evictions story written by Big Local News. 

A large portion of our story focuses on evictions as they relate to Public Housing Authorities.

When initially deciding which counties to focus on, we took the public housing spreadsheet which identifies all public housing authorities in California. We then took rent burden information to calculate which counties had the highest rent burdens & had public housing authorities in the county. 

From there, we got a list of high rent burden counties which we focused on for our analysis. 

Notebook ‘finding_ambiguous_counties.ipynb’ helps us do some preliminary data cleaning to identify cities that have been assigned to the wrong county & correct the data. 
Notebook ‘hard_hit_draft3.ipynb’ has the full analysis of the data.

cali_hist_data.ipynb - historical data grabbed from the layoffs site (2014-2020) - re compare this and check scraper to see if all of the data is still there, if not, fix so that we can have all the same data


winnow_counties.ipynb - Takes ACS 2018 5 year estimates information on households paying a % of their income in rent. We take the # of households paying more than 50% rent to calculate counties with the highest rent burdens. (‘ACS_2018_5year_est.csv’) is the file it takes in, (‘ACS_2018_5year_rentburden.csv’) is the file it produces.

rent_burden_calc.ipynb -  This notebook adds (‘ACS_2018_5year_median_gross_rent_percent_of_income.csv’) and (‘Housingauthorities.csv’)  to look at median gross rent as a percentage of household income for each county. Then it is combined with the  (‘ACS_2018_5year_rentburden.csv’) file from the winnow_counties.ipynb to identify which counties have a high rent burden that overlap with counties with public housing authorities. This results in the csv (‘rent_burden_households_and_median_gross_rent_percent.csv’) which helped us decide which counties to look into based on high rent burden and public housing authorities.