# Housing Affordability In New York State (2013-2023)

## Overview
The purpose of this report is to grasp housing affordability changes in New York State between 2013 and 2023. In particular, the analysis will quantify the changes. Over the past few years, the real estate market has been really hot. This has caused residential real estate and mortgage interest rates to escalate at a rapid pace. Moreover, the increase price tag on residential real estate has prompted Landlords to increase monthly rent payments, potentially making housing less affordable for non-homeowners.

### Why Housing Affordability in New York State?
For many Americans, homeownership is crucial to their financial well-being. After all, it is one of the biggest achievements sought after in accordance with the American Dream. Homeownership has also been a tool used to build generational wealth. Moreover, homeownership is not for everyone, and therefore, renting affordability is just as important for many.

### Questions We Hope to Answer:
* In recent years, how much has housing affordability changed in New York?
  * What does it look like for homeownership?
  * What does it look like for residential rentals?


### About the Data
* Housing Price datasets:
  1. Rental Zillow data – Median Sale Price (Raw, Monthly):
      - https://www.zillow.com/research/data/
  2. Home Sale Price Zillow data – ZORI: All Homes Plus Multifamily Time Series:
      - https://www.zillow.com/research/data/
* Wage datasets:
  1.	Bureau of Labor Statistics (BLS) – Annual County Data: Excel File Format
      - https://www.bls.gov/cew/downloadable-data-files.htm

### Tools Used:
* Python: an interpreted, object-oriented, high-level programming language.
* Pandas: a library built upon NumPy that allows data scientists to clean and transform data structures.
* NumPy: the data will require some arithmetic across many datapoints and NumPy’s broadcasting operation ability will facilitate this task.
* Plotly/Seaborn/Matplotlib: visualizations will tell the stories and trends found within the dataset.
* Datetime: will allow for proper interpretation and alignment of date values across multiple datasets to visualize and organize data.

### Data Preprocessing
The following data transfomation techniques took place:
* Bucketing.
* Reshaping between long and wide format.
* Data type tranformation.
* Filtering to specific values directly, through conditions, masking, or pandas method checks (e.g.: isin())
* Handling missing values.
* Creating custom calculated fields.

#### Data Challenges
An unusual data challenge was identifying annual average wage data for New York State regions. The only reputable source found is from the Bureau of Labor Statistics and it is limited through 2021. However, the freely available API does not provide the aggregate and selection features a Data Scientist would expect. A work around was to use a series of excel workbooks directly from the website. It was retrieved by downloading it directly to a workstation directory and later consolidated into one Pandas DataFrame through a sequence of custom Python functions and iterations.


## Results

### Homeownership

The median residential home sale price was found be me mostly flat with a slight positive slope between 2013 and early 2019, but in the middle of 2019 a surge in sale price ensued. Despite this, there seems to have been a peak mid 2022.

![Median Residential Home Sale Price in Select New York Regions (2013-2023)](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Median_Residential_Home_Sale_Price_in_Select_New_York_Regions_(2013-2023).png?raw=true)


The median home sale price increased an average of $85,419.28. With _New York, NY_ and _Binghamton, NY_ having the highest and lowest increases, respectively. Cost increase were also calculated and _Poughkeepsie, NY_ was found to have the highest percent increase in cost.

![Median $ Price Change Between 2013 and 2023](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Median_$_Price_Change_Between_2013_and_2023.png?raw=true)

![Median % Price Change Between 2013 and 2023](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Median_%25_Price_Change_Between_2013_and_2023.png?raw=true)

![Table - Median Home Price Change Between 2013 and 2023](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/df_median_sale_price_delta.png?raw=true)


A particular factor explored to try to deduce real homeownership affordability was the average monthly interest rate for 30-year mortgage loans. Interestingly, the sharp decrease in interest rate at the end of 2018 aligns with the aforementioned surge in the median sale price of homes. On the contrary, the newly implemented high interest rate also aligns with the decline in median home sale price. Morever, it was found that although cost of home sale prices have only increased a minimum of approximatly 32%, when evaluated with the elevated interest rate, homeowners are now paying twice as much every month (apprx. 100% increase). The payments were calculated by using the [Annuity Formula](https://www.investopedia.com/retirement/calculating-present-and-future-value-of-annuities/).

![Average Monthly Mortgage Rates in the US (2013-2023)](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Average_Monthly_Mortgage_Rates_in_the_US_(2013-2023).png?raw=true)

[Estimated Monthly Mortgage Cost Visualization By Region](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Estimated_Monthly_Payments_by_Region_(2013-2023).png?raw=true)


### Rental Cost

Rent cost information was found to be limited. **Data was only available beginning March of 2015**, and many datapoints are null. It is still worthy to note that rent cost had a sharp decline in _New York, NY_ at the height of the COVID-19 pandemic. On the other hand, some other New York State regions had the opposite effect; a surge in rent cost. As expected, _Poughkeepsie, NY_ also had the highest increase in rent cost.

![Median Price of Rental Homes in Select New York Regions Over Time](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Median_Price_of_Rental_Homes_in_Select_New_York_Regions_Over_Time.png?raw=true)

![Median $ Price Change Between March 2015 and February 2023](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Rent_-_Median_$_Price_Change_Between_March_2015_and_February_2023.png?raw=true)

![Rent - Median % Price Change Between March 2015 and February 2023](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Rent_-_Median_%25_Price_Change_Between_March_2015_and_February_2023.png?raw=true)

![Table - Median Rent Cost Delta](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/df_median_rent_cost_delta.png?raw=true)

### Wage Trends

Data from the Bureau of Labor Statistics was used. Data for wages in the U.S., as well as New York Statewide were also extracted to help better gauge wage increases. **This dataset is also limited through the year 2021.** Overall, it was found that wages have increased nationwide. Overall, New York State regions have had wage increases below the nationwide total. Overall, all regions have had approximately 21%-28% increase in wages. _New York, NY_ had the highest change with a 35% increase which is expected given the recent diaspora of millionaires, billionaires, and the increase in high paying jobs in the technology sector.

![Average Annual Wages in Select New York State Regions](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Average_Annual_Wages_in_New_York_State.png?raw=true)

![Average $ Annual Wage Change Between 2013 and 2021](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Average_$_Annual_Wage_Change_Between_2013_and_2021.png?raw=true)

![Average % Annual Wage Change Between 2013 and 2021](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/Average_%25_Annual_Wage_Change_Between_2013_and_2021.png?raw=true)

![Table - Average Wage Delta](https://github.com/jlixander/nys_housing_affordability/blob/main/graphs_and_tables/df_average_wage_delta.png?raw=true)


## Summary

In the last 10 years, housing affordability in New York has dwindled significantly. Home sale prices have seen an increase between ~32% and 48%. The true monthly cost has almost doubled in most regions when accounting for increased interest rates. Although not at the same rate as homeownership, rent affordability has also decreased over time.


## Potential Next Steps in Analysis
* Explore minimum wage affordability separately.
* Analyze affordability by annual wage ranges (Bins).
* Account for annual property, school, and homeowner insurance cost.
* Use median wage data instead of average as it may introduce skewness.
* Evaluate areas segregated by metro, suburban, and rural regions as each may have its unique outliers.
* Use more complete datasets.




## Resources
1. Zillow, 2020
2. Bureau of Labor Statistics (BLS)

### GitHub Repository
https://github.com/jlixander/nys_housing_affordability/tree/main
