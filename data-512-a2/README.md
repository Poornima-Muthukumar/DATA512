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
| Data(M)                 |                                             |
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


## Data Analysis:

## Libraries Used:
1. matplotlib
2. pandas
3. json
4. requests
5. csv
