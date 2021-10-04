**Description: **

The goal of this project is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2021
For this project, we combine data about Wikipedia page traffic from two different Wikimedia REST API endpoints into a single dataset, perform some simple data processing steps on the data, and then analyze that data.


**Data Source:**
In order to measure Wikipedia traffic from 2008-2021, we collect data from two different API endpoints, the Legacy Pagecounts API and the Pageviews API.

The Legacy Pagecounts API (documentation, endpoint) provides access to desktop and mobile traffic data from December 2007 through July 2016.

The Pageviews API (documentation, endpoint) provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.


**Data Acquisition: **
For each API, we collect data for all months where data is available and then save the raw results into 5 separate JSON source data files (one file per API query type.

we're interested in organic (user) traffic, as opposed to traffic by web crawlers or spiders. The Pageview API (but not the Pagecount API) allows you to filter by agent=user.

The JSON files collected are - 

1. pagecounts_desktop-site_200801-201607.json: Desktop page counts (legacy) from January 2008 to July 2016
2. pagecounts_mobile-site_200801-201607.json: Mobile site page counts (legacy) from January 2008 to July 2016. Note mobile data is only available from October 2014
3. pageviews_desktop-site_201507-202108.json: Desktop Page Views from July 2015 to August 2021
4. pageviews_mobile-web-site_201507-202108.json: Mobile Web Page Views from July 2015 to August 2021
5. pageviews_mobile-app-site_201507-202108.json: Mobile App Page Views from July 2015 to August 2021


**Data Processing:**
We will perform some data processing on these data files to prepare them for analysis.

1.Combine monthly values for mobile app and mobile web from pageview api.
2.Separate the value of timestamp into (YYYY) and (MM) and discard (DDHH)
3.If no traffic is available for a given access method, mark it as 0.
4.Combile all data in one file for analysis.

We combile all the pageviews into one csv file - en-wikipedia_traffic_200712-202108.csv

The combined CSV has the columns - 


**Data Analysis:**
**Libraries Used:**
1. 