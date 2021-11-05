# mapping_lats

Welcome to mapping_lats. In this repository, we're demonstrating how to use python, pandas, geopandas, and data from the census bureau and kaggle to try and understand where we're likely to see Chipotle Restaurants. This project focuses California counties and the variation in housing prices only. 

Step 1. - Look for the datasets you want. 
In our case, we're interested in understanding where we'll find Chipotles in California. 
1. Kaggle Dataset on Chipotle Locations: https://www.kaggle.com/jeffreybraun/chipotle-locations
      Thanks to Jeffrey Braun for posting this data on kaggle!

2. Census Buerau API - https://www.census.gov/data/what-is-data-census-gov/guidance-for-data-users/how-to-materials-for-using-the-census-api.html  
      We'll register for an API token and use requests.get method to download specific data that we're looking for. 

3. Tigerline Shape files - https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html
      We'll download the tiger line shape files as we'll need to merge our Chipotle stores Lat/Lng with our county shape files to understand where Chipotles are located on the county level.
      
Step 2. - Cleaning
1. The raw data file from the Census Buerau API needs relabeling. We'll look to their helpful documentation on what columns need to be relabeled. https://api.census.gov/data/2018/acs/acs5/groups/B25075.html 
Changing population numbers from our Census Bureau API to fractions of the total will help us get a better understanding of where Chipotles are at the aggregate level. This corrects for counties with very large or very small populations. 
Additionally, we'll need to clean the tigerline shape files, and remove unnecessary categories. 
Finally, make sure everything is either a string or numeric. Difficulties with merging will occur if the 

Step 3. - Merging
1. Downloading GeoPandas is required for this step. You'll need to spatially join our Chipotle store locations' latitudes and longitudes onto the tigerline counties. https://geopandas.org/index.html

Step 4. - Analysis
1. Thanks to the hard work of the authors at this link - https://ai-ml-analytics.com/multicollinearity-with-ordinary-least-squares/
we can use Ordinary Least Squares and VIF method to determine if housing prices predict physical Chipotle restaurant locations. Unfortuantely, they don't. We'll need to circle back and pick features that have fewer multicolinearities and redo our analysis. 

