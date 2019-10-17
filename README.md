# GOAL
The goal of this assignment was to find out if there are any biases in the dataset that is obtained from wikipedia. We study 2 different datasets, to see which countries in the world have publised the best articles and which countries have a higher articles:population ratio.

# Dataset Source
We used to datasets in this analysis, both of which are provided in this repository.
The first one is the WPDS_2018_data.csv. It contains the following fields:
1. Geography: This contains the names of the continents (regions) and their countries
2. Population mid-2018 (millions): This contains the repspective populations of the countries and the regions

The second file is the page_data.csv. It contains the following fields:
1. page: This contains the name of the article. There are some cases where the name starts with 'Template'. We have ignored these in our analysis
2. country: This field contains the names of the countries from which these articles were written.
3. rev_id: This is the revision_id of the article, which is used to get the ORES score for that article.

# Files generated
The following files have been generated during the analysis phase:
wp_wpds_countries-no_match.csv: This file contains the records for which we do not have either the population information, or those countries who do not have any articles. This file contains the following fields:
1. country: Contains the names of the countries
2. Population: Contains the population of the countries if we have the population for these countries.
3. rev_id: Contains the revision ids for the articles for those articles, for which we have revision_ids

wp_wpds_politicians_by_country.csv: This file contains all the records that are used in the analysis. All data is present for this file. This file has the following fields:
1. country: The name of the country the article comes from
2. page: The name of the wikipedia page
3. article_quality: This contains the class in which these articles are classified into, namely: FA - Featured article, GA - Good article, B - B-class article, C - C-class article, Start - Start-class article, Stub - Stub-class article.
4. rev_id: This contains the revision id for the articles.
5. Population: This contains the population of the country.

# API
The following API was used for generating the predictions for all the articles with revision_ids:
[ORES REST API](https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model)

# RESULT
The result contains 6 tables that show:
1) Top 10 countries by coverage: Top 10 countries ranked by the total number of articles divided by the population of the country.
2) Bottom 10 countries by coverage: Bottom 10 countries ranked by the total number of articles divided by the population of the country.
3) Top 10 countries by relative article quality: Top 10 countries ranked by the ratio of number of GA/FA articles divided by total number of articles in the country.
4) Bottom 10 countries by relative article quality: Bottom 10 countries ranked by the ratio of number of GA/FA articles divided by total number of articles in the country.
5) Geographical regions based on coverage: Descending order of geographical regions based on number of articles in the region divided by the population of the region.
6) Geogrphical regions based on relative article quality: Descending order of geographical regions based on number of GA/FA articles in the region divided by the total number of articles in the region.
