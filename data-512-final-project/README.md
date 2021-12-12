# Impact of COVID-19 on Housing Market in Mecklenburg County, North Carolina

# Abstract
In this project, I plan to analyze the impact of covid on the housing market. One specific area that specifically experienced the brunt of this unprecedented crisis is the housing market. As a home buyer during the pandemic, my husband and I were going through the process of searching for a home. But the housing market at the start of 2021 gave us immense anxiety and worry as the demand for the houses was very high, prices of the houses kept escalating at a very fast rate, the inventory of houses kept declining and the bidding war to top it off made things worse. We spent countless hours every day trying to read the news, watching youtube videos, and talking to other buyers to understand the housing market to help with the confusion.

A lot of the home-buyers across the country are frustrated with this increasing trend in housing prices. This topic is particularly human-centered as it affects a vast majority of Americans who are looking to purchase homes. If the prices keep increasing at this rate, a lot of the people from lower-income brackets will suffer as they will not be able to afford to house, or will be pushed to outskirts or suburbs thus causing a widening of the wealth gap between the rich and the poor. Because homeownership is an important tool for building long-term wealth and children of homeowners are likely to become homeowners, this trend can further exacerbate wealth inequality for future generations.

By performing this analysis I hope to learn if there was any correlation between the number of covid cases and housing prices and hope to see how the market fluctuated during the pandemic. I also want to see if the housing prices have gone down recently or if they are still on the increasing trend. This analysis is of particular scientific interest as it will help others see trends between housing prices and a fluctuating economy during a pandemic.

# Research Question and Analysis
As the pandemic progressed, the cases started increasing nationwide. The state and national government issued several lockdowns to control the spread of the virus, a lot of the businesses were shut and there was widespread fear of another recession. Tracking changes in the housing market will provide us insights into the economy of North Carolina state, help us contextualize growth and decline in this county, and give us insight into the market. As part of this project, I plan to explore the following questions to help understand the trend in the housing market since the start of the pandemic.

1. During the COVID-19 pandemic did the housing prices go up or down from January 2020 through August 2021?
2. Did the number of COVID-19 cases and deaths have an impact on the housing prices from January 2020 through August 2021?
3. Where there any other trends in the data related to covid cases and the housing market?

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

3. The monthly housing market data from Redfin - https://redfin-public-data.s3.us-west-2.amazonaws.com/redfin_market_tracker/county_market_tracker.tsv000.gz
4. 30 year fixed Interest Rate - https://fred.stlouisfed.org/series/MORTGAGE30US

# Methodology

### Correlation between covid cases and housing prices 
Here I will perform exploratory data analysis by creating visualizations to see the correlation between housing market data and covid cases week over week.  

Here I will plot the following visualization from the redfin data set. 
Weekly confirmed covid cases and the number of new listings.
Weekly confirmed covid cases and the total number of homes sold.
Weekly confirmed covid cases and inventory.
Weekly confirmed covid cases and median sale price.

 ### Linear Regression
I will also perform linear regression to predict housing prices for 2020 and 2021 and compare it with actual housing prices to see if there is a difference between predicted and actual housing prices for 2020 and 2021. 

Linear regression suits best to find the relationship between a dependent continuous variable (Median Sale Price) and one or more explanatory independent variables (Month/Year). Linear regression suits best here because we can see a linear trend in the dataset for housing prices and housing prices are normally distributed. 

I will fit a univariate linear regression model using historical data from (2013- 2019)  where the feature is the monthly dates and the target is the median housing price. We are all aware of the housing market crash in 2007-2008 and it took the market some time to stabilize after the crash, hence I have decided to train the model with data post-2010.  I will split the data into (80-20 train test split) and fit a linear regression model using python scikit learn. I will also compute the RMSE (root mean square error) as a measure of model performance and use the model to predict housing prices for 2020 and 2021 and compare if the prediction is higher or similar to actual prices. 

# Summary Plots and Visualization

### Findings
 **Housing Inventory**: During the pandemic in 2020 and 2021, we can see a sharp decline in housing inventory (blue line) since January 2021(peak of covid) as seen on the red line. A decline in inventory was caused by multitude of reasons such as decline in new constructions due to supply chain disruptions, people not wanting to sell homes due to economic uncertainty, people not wanting to sell homes to avoid home visits by strangers to avoid contracting the virus, and also because of strict stay at home orders and lockdowns in place by the government. 
 
![plot1](https://github.com/Poornima-Muthukumar/DATA512/blob/master/data-512-final-project/images/correlation/weekly_cases_vs_house_inventory_mecklenburg_county.jpeg)

**Median Sale Price**:  We can see an upward trend in median housing prices overall in NC. The housing price dipped briefly around January 2021 when the cases peaked, but it steadily increased after that. We can see a 100K increase in median sale price in a span of roughly two years from 260k to 360k. The increase in Median Sale Price can be correlated to the decline in inventory as can be seen from the above graph. 

![plot3](https://github.com/Poornima-Muthukumar/DATA512/blob/master/data-512-final-project/images/correlation/weekly_cases_vs_median_sale_price_mecklenburg_county.jpeg)

**Total Number of Homes Sold and Total Number of New Listings:**  The graph on the left shows the fluctuations in the total number of homes sold.  We can see at the start of the pandemic the number of homes sold were lower as there was an overall uncertainty due to the pandemic. Around June 2020 we can see the number of homes sold start to increase and then it dips when the number of covid cases reaches its peak around January 2021. Similarly, we can see a sharp drop in the number of new listings around January 2021 when the cases peak. From these two graphs, we can conclude that everytime the COVID cases increase the number of homes sold and number of new listings in the market decrease. This could be caused by a number of factors like lockdown, fear among people of getting covid by doing home tours, sellers thinking they might not be able to sell at a high price if there are not enough buyers, real-estate agents not wanting to do in-person home tours etc. 

![plot2](https://github.com/Poornima-Muthukumar/DATA512/blob/master/data-512-final-project/images/correlation/weekly_cases_vs_houses_sold_mecklenburg_county.jpeg)

![plot4](https://github.com/Poornima-Muthukumar/DATA512/blob/master/data-512-final-project/images/correlation/weekly_cases_vs_new_listing_mecklenburg_county.jpeg)

### Linear Regression

From the output of the linear regression model, we can see that there is roughly 100K difference between the actual housing and predicted housing price for 2020 and 2021. The model was trained with historic housing price data from (2013 to 2019) and based on that was asked to predict the housing price for 2020 and 2021. The model output shows that the housing price during the pandemic increased significantly more compared to previous years and that houses sold for a higher price than they should have been.

![plot4](https://github.com/Poornima-Muthukumar/DATA512/blob/master/data-512-final-project/images/linearregression/linear_regression_line_median_sale_price.jpeg)

![plot4](https://github.com/Poornima-Muthukumar/DATA512/blob/master/data-512-final-project/images/linearregression/actual_vs_predicted_price_validation_set.jpeg)

   | Year                        | % Change                               |
   |-----------------------------|----------------------------------------|
   | 2014                        | 0.026586                               |
   | 2015                        | 0.051282                               |
   | 2016                        | 0.131707                               |
   | 2017                        | 0.012931                               |
   | 2018                        | 0.089362                               |
   | 2019                        | 0.050781                               |
   | 2020                        | 0.222770                               |
   | 2021                        | 0.194801                               |

# Conclusion:
Through my analysis, I can conclude that the COVID-19 pandemic had an impact on the housing market in Mecklenburg County. We can see that COVID-19 pandemic has impacted both supply and demand in the housing market.  People wanted to take advantage of lower mortgage rates which caused the demand for housing to go up.

However the pandemic also fueled a shortage in supply of homes - both newly built and those sold by existing owners.  We can see a decline in housing inventory, number of new listings on the market as covid cases increased.  Thus we can conclude that an increased demand and a shortage in supply fueled the median sale price of the homes to go up throughout the pandemic. 

To conclude, this study informs the reader of their understanding of human centered data science as it is important to pay attention to this trend and for the government to take action. It is important to fix this gap between supply and demand by building more homes where people need it, otherwise this inequality will continue to skyrocket and a growing number of Americans will be shut out of the housing market altogether.

# Limitations
1. All my analysis and conclusions are based on Single Family Homes (SFH). This could mean that there could be other patterns and trends for different property types and my results do not extend to other residential properties such as condos, townhomes, etc
2. In my interest rate analysis, I focus on the 30 year fixed interest rate. This could mean that other interest rates could have influenced the housing market differently which is not explored in my analysis. 
3. The analysis uses a 7 day rolling average number of covid cases to see correlation between the number of covid cases and housing market and does not include deaths. 
4. The Redfin weekly and monthly data is not seasonally adjusted. Doing so could yield slightly different results. 

# Future Work
Future Work
1. It will be interesting to build on top of my analysis to see patterns in the housing market related to other factors such as work from home, commuting patterns, supply chain disruptions, wood prices, lockdown restrictions that have also had some impact on the housing market indirectly.
2. Another interesting future work is to see how the housing market performed in different states and counties and if there was any commonality that can be extended from such an analysis to generalize the results with similar size states and counties.
3. Another potential analysis involves how rental prices fluctuated throughout the pandemic and if there was any correlation between rental price and housing prices.
4. Another analysis that can be built on top of this includes looking at the median household income of the people purchasing the homes to further analyse how the government can create schemes to help racial and generational inequality. 
5. Going forward it would also be useful to put this visualization in a dashboard that gets refreshed with data on a day-to-day basis so we can see how the housing market evolved as COVID and its variants and cases change on a timely basis. 


# License
  My research would be released under an MIT License and the data is all public domain.

# Folder Structure
```
.
├── README.md
├── data_processed
│   └──covid-data-mecklenburg-cleaned.csv
|   └──housing-data-mecklenburg-cleaned.csv
|   └──housing-covid-merged.csv
├── data_raw
│   └──CONVENIENT_us_confirmed_cases.csv
|   └──CONVENIENT_us_deaths.csv
|   └──MORTGAGE30US.csv
|   └──RAW_us_confirmed_cases.csv 
│   └──mask-use-by-county.csv
├── results
│   └── ProjectPresentation.pptx
|   └── Common-Analysis-Reflection.doc
|   └── Final-Project-Report.doc
├── src
│   └── poornima-muthukumar-a4.ipynb
|   └── poornima-muthukumar-final-project.ipynb
├── images
|   ├──commonanalysis
|   |    └── 7Day_Average_Deaths_Mecklenburg_North_Carolina.jpeg 
|   |    └── Cumulative_Cases_Deaths_Mecklenburg_North_Carolina.jpeg
|   |    └── Mecklenburg-County-NC-Cumulative-Cases.jpeg 
|   |    └── Mecklenburg-County-NC-Rate-Of-Infection.jpg
|   ├──linearregression
|   |    └── median_sale_prie_mecklenburg_county.jpeg
|   |    └── linear_regression_line_median_sale_price.jpeg
|   |    └── test_set_actual_vs_predicted_price.jpeg
|   |    └── actual_vs_predicted_price_validation_set.jpeg
|   └──correlation
|   |    └── weekly_cases_vs_house_inventory_mecklenburg_county.jpeg
|   |    └── weekly_cases_vs_houses_sold_mecklenburg_county.jpeg
|   |    └── weekly_cases_vs_median_sale_price_mecklenburg_county.jpeg
|   |    └── weekly_cases_vs_new_listing_mecklenburg_county.jpeg
└── LICENSE

```
# Libraries Used:
1. pandas
2. numpy
3. json
4. requests
5. matplotlib
6. sklearn

# References
  1. Federal Reserve Bank of St. Louis. (2021, December 9). The impact of covid-19 on the residential real estate market: St. Louis Fed. Saint Louis Fed Eagle. Retrieved December 11, 2021, from https://www.stlouisfed.org/publications/regional-economist/fourth-quarter-2020/impact-covid-residential-real-estate-market. 
   2. Demsas, J. (2021, February 5). Covid-19 caused a recession. so why did the housing market boom? Vox. Retrieved December 11, 2021, from https://www.vox.com/22264268/covid-19-housing-insecurity-housing-prices-mortgage-rates-pandemic-zoning-supply-demand. 
  3. Sai Balasubramanian, M. D. (2021, December 10). The COVID-19 pandemic has fueled a crisis in the housing market. Forbes. Retrieved December 11, 2021, from https://www.forbes.com/sites/saibala/2021/04/27/the-covid-19-pandemic-has-fueled-a-crisis-in-the-housing-market/?sh=49f3de175928. 
4. Valkov, V. (2019, July 5). Predicting house prices with linear regression: Machine learning from scratch (part II). Medium. Retrieved December 11, 2021, from https://towardsdatascience.com/predicting-house-prices-with-linear-regression-machine-learning-from-scratch-part-ii-47a0238aeac1. 
5. Faressayah. (2021, August 5). Linear regression 📈 house 🏡 price 💵 prediction. Kaggle. Retrieved December 11, 2021, from https://www.kaggle.com/faressayah/linear-regression-house-price-prediction. 
6. The impact of coronavirus on the U.S Housing Market - Redfin. (n.d.). Retrieved December 11, 2021, from https://www.redfin.com/guides/coronavirus-housing-market-impact. 

# Human Centered Data Science Perspective
In my analysis, I have made an effort to address a variety of human-cenetered data science considerations including:

1. Licenses: I ensured that the research is licensed under a MIT license so others can use it.
2. Copyright: Appropriately citing sources of data, tools, and inspiration
3. Interpretability: Following a literate programming style to explain decisions made along the way that impact the final results of my analysis
4. Reproduciblity: Making my research reproducible by providing information about my environment, how I used the data, and where I received my data in addition to including my data in my repository so that anyone could run my notebooks to replicate my results
5. Interpretability: I hav used methods like Linear regression that are very transparent and easy to understand for the audience of the research. Also I have used visualisation to convey the informaion in a simple manner to promote this goal.

