# Impact of COVID-19 on Housing Market

# Abstract
In this project, I plan to analyze the impact of covid on the housing market. One specific area that specifically experienced the brunt of this unprecedented crisis is the housing market. As a home buyer during the pandemic, my husband and I were going through the process of searching for a home. But the housing market at the start of 2021 gave us immense anxiety and worry as the demand for the houses was very high, prices of the houses kept escalating at a very fast rate, the inventory of houses kept declining and the bidding war to top it off made things worse. We spent countless hours every day trying to read the news, watching youtube videos, and talking to other buyers to understand the housing market to help with the confusion.

A lot of the home-buyers across the country are frustrated with this increasing trend in housing prices. This topic is particularly human-centered as it affects a vast majority of Americans who are looking to purchase homes. If the prices keep increasing at this rate, a lot of the people from lower-income brackets will suffer as they will not be able to afford to house, or will be pushed to outskirts or suburbs thus causing a widening of the wealth gap between the rich and the poor. Because homeownership is an important tool for building long-term wealth and children of homeowners are likely to become homeowners, this trend can further exacerbate wealth inequality for future generations.

By performing this analysis I hope to learn if there was any correlation between the number of covid cases and housing prices and hope to see how the market fluctuated during the pandemic. I also want to see if the housing prices have gone down recently or if they are still on the increasing trend. This analysis is of particular scientific interest as it will help others see trends between housing prices and a fluctuating economy during a pandemic.

# Research Question and Analysis
As the pandemic progressed, the cases started increasing nationwide. The state and national government issued several lockdowns to control the spread of the virus, a lot of the businesses were shut and there was widespread fear of another recession. Tracking changes in the housing market will provide us insights into the economy of North Carolina state, help us contextualize growth and decline in this county, and give us insight into the market. As part of this project, I plan to explore the following questions to help understand the trend in the housing market since the start of the pandemic.

During the COVID-19 pandemic did the housing prices go up or down from January 2020 through August 2021?
Did the number of COVID-19 cases and deaths have an impact on the housing prices from January 2020 through August 2021?
Where there any other trends in the data related to covid cases and the housing market?

# Data Sources
To perform the analysis I will use the following different datasets.

1. The RAW_us_confirmed_cases.csv file from the Kaggle repository of John Hopkins University COVID-19 data - https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university?select=RAW_us_confirmed_cases.csv

2. The weekly housing market data from Redfin - https://redfin-public-data.s3-us-west-2.amazonaws.com/redfin_covid19/weekly_housing_market_data_most_recent.tsv

The Redfin weekly housing market data has data for each county on a weekly basis. The data is broken down by property type (All Residential, Single Family, Condo, Multi-Family, Townhouse, etc). Redfin has published [this page](https://www.redfin.com/news/data-center-metrics-definitions/) to define each column in the dataset and how to interpret the column. This data set is licensed under [Redfin’s Terms of Use](https://www.redfin.com/about/terms-of-use). The guidelines for using the data states to cite the data source appropriately and provide a link to Redfin.

| Column                      | Values                                 |
|-----------------------------|----------------------------------------|
| period_begin                | Start date                             |
| period_end                  | End date                               |
| inventory                   | Housing Inventory                      |
| total_homes_sold            | Total Homes Sold                       |
| median_sale_price           | Median Sale Price                      |
| median_new_listing_price    | Median New Listing Price               |
| total_new_listings          | Total New Listing                      |

# Methodology

# Correlation between covid cases and housing prices 
Here I will perform exploratory data analysis by creating visualizations to see the correlation between housing market data and covid cases week over week.  

Here I will plot the following visualization from the redfin data set. 
Weekly confirmed covid cases and the number of new listings.
Weekly confirmed covid cases and the total number of homes sold.
Weekly confirmed covid cases and median list price.
Weekly confirmed covid cases and median sale price.

# Linear Regression
I will also perform linear regression to predict housing prices for 2020 and 2021 and compare it with actual housing prices to see if there is a difference between predicted and actual housing prices for 2020 and 2021. 

Linear regression suits best to find the relationship between a dependent continuous variable (Median Sale Price) and one or more explanatory independent variables (Month/Year). Linear regression suits best here because we can see a linear trend in the dataset for housing prices and housing prices are normally distributed. 

I will fit a univariate linear regression model using historical data from (2010- 2019)  where the feature is the weekly dates and the target is the median housing price. We are all aware of the housing market crash in 2007-2008 and it took the market some time to stabilize after the crash, hence I have decided to train the model with data post-2010.  I will split the data into (80-20 train test split) and fit a linear regression model using python scikit learn. I will also compute the RMSE (root mean square error) as a measure of model performance and use the model to predict housing prices for 2020 and 2021 and compare if the prediction is higher or similar to actual prices. 

# Conclusion

# Issues

# Future Work

# License
My research would be released under an MIT License and the data is all public domain.

# Files Cheked In

# Libraries Used:
1. pandas
2. numpy
3. json
4. requests
5. matplotlib
6. sklearn

# References

# Human Centered Data Science Perspective
