## Description:
The goal of this project is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries. For this project, we will combine a dataset of Wikipedia articles with a dataset of country populations, and use a machine learning service called ORES to estimate the quality of each article.

## Data Source:
1. **The Wikipedia politicians by country dataset** can be found on [Figshare](https://figshare.com/articles/dataset/Untitled_Item/5513449). Read through the documentation for this repository, then download and unzip it to extract the data file, which is called page_data.csv.

| Column                  | Values                                      |
|-------------------------|---------------------------------------------|
| page                    | article name                                |
| country                 | country the politician belongs to           |
| rev_id                  | Revision ID of the last edit to the article |

2. **The population data** is available in CSV format as [WPDS_2020_data.csv](https://docs.google.com/spreadsheets/d/1CFJO2zna2No5KqNm9rPK5PCACoXKzb-nycJFhV689Iw/edit#gid=283125346). This dataset is drawn from the [world population data sheet](https://www.prb.org/international/indicator/population/table/) published by the Population Reference Bureau.

| Column                  | Values                                      |
|-------------------------|---------------------------------------------|
| FIPS                    | Country Code                                |
| Name                    | Country Name                                |
| Type                    | Type                                        |
| TimeFrame               | Year                                        |
| Data(M)                 | Population (millions)                       |
| Population              | Population of the Country                   | 

## Data Acquisition: 
Now you need to get the predicted quality scores for each article in the Wikipedia dataset. We're using a machine learning system called [ORES](https://www.mediawiki.org/wiki/ORES). This was originally an acronym for "Objective Revision Evaluation Service" but was simply renamed “ORES”. ORES is a machine learning tool that can provide estimates of Wikipedia article quality. The article quality estimates are, from best to worst:

  1. FA - Featured article
  2. GA - Good article
  3. B - B-class article
  4. C - C-class article
  5. Start - Start-class article
  6. Stub - Stub-class article

## Data Processing:
Some processing of the data will be necessary! In particular, you'll need to - after retrieving and including the ORES data for each article - merge the wikipedia data and population data together. Both have fields containing country names for just that purpose. After merging the data, you'll invariably run into entries which cannot be merged. Either the population dataset does not have an entry for the equivalent Wikipedia country, or vise versa.

Please remove any rows that do not have matching data, and output them to a CSV file called:
wp_wpds_countries-no_match.csv

Consolidate the remaining data into a single CSV file called:
wp_wpds_politicians_by_country.csv

The schema for that file should look something like this:

| Column                  | 
|-------------------------|
| country                 | 
| article_name            | 
| revision_id             | 
| article_quality_est     |
| population              |                                             

## Data Analysis:
Your analysis will consist of calculating the proportion (as a percentage) of articles-per-population and high-quality articles for each country AND for each geographic region. By "high quality" articles, in this case we mean the number of articles about politicians in a given country that ORES predicted would be in either the "FA" (featured article) or "GA" (good article) classes.

Examples:
if a country has a population of 10,000 people, and you found 10 FA or GA class articles about politicians from that country, then the percentage of articles-per-population would be .1%.
if a country has 10 articles about politicians, and 2 of them are FA or GA class articles, then the percentage of high-quality articles would be 20%.

## Reflection
Looking the ranking of countries it is not surprising to see that countries which are smaller in size with small population are ranked higher. Tuvalu with a population of only 10000 has 54 articles. It is surprising to see such a smaller country with so many articles.

Similarly countries lower in the rank are the countries with largest population like China and India. The number of politicians in a country is not directly proportional to the population of the country thereby resulting in lower ratio when compared to smaller nations.

Also it is possbile that in countries like China and India, the people prefer writing articles in their local languages thereby resulting in lower Engligh wikipedia articles.

The fact that North Korea stood out as the country with the highest good quality articles could be because these articles are infact written by americans given the increased interest among americans with North Korea.

## Libraries Used:
1. matplotlib
2. pandas
3. json
4. requests
5. csv
