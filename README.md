# mapping_lats

Welcome to mapping_lats. This repository demonstrates the use of python, pandas, geopandas, and data from the census bureau and kaggle to understand where we're likely to see Chipotle restaurants. This demonstration focuses on California counties, their variations in housing prices, and the preponderance of Chipotles in those counties. Below is a high level run through on how to perform this task. Look to the jupyter notebook for further details.

Step 1. - Download the datasets. 
In our case, we're interested in understanding where we'll find Chipotles in California. 
1. Kaggle Dataset on Chipotle Locations - https://www.kaggle.com/jeffreybraun/chipotle-locations
      Thanks to Jeffrey Braun for posting this data to kaggle!

2. Census Buerau API - https://www.census.gov/data/what-is-data-census-gov/guidance-for-data-users/how-to-materials-for-using-the-census-api.html  
      We'll register for an API token and use requests.get method to download the specific data that we're looking for. 

3. Tigerline Shape files - https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html
      We'll download the tiger line shape files as we'll need to merge our Chipotle stores Lat/Lng with our county shape files to understand where Chipotles are located at the county level.
      
To reduce the difficulty of wrangling with the Census Bureau API and Tiger Line Shape Files, or just to speed up your process (if time is of the essence), you can download preset data and shape files from the Census Reporter https://censusreporter.org. While knowing how to navigate the API is helpful, the censusreporter expedites this step significantly. 
      
Step 2. - Cleaning
1. The raw data file from the Census Buerau API needs relabeling. We'll look to their helpful documentation on what each column stands for. https://api.census.gov/data/2018/acs/acs5/groups/B25075.html 
Changing population numbers from our Census Bureau API to fractions of the total will help us better understand where Chipotles are at the aggregate level. This corrects for counties with very large or very small populations. 
Additionally, we'll need to clean the tigerline shape files and remove unnecessary categories. 
Finally, make sure everything is either a string or numeric. Difficulties with merging will occur if the datatypes do not match.

Step 3. - Merging
1. Downloading GeoPandas is required for this step. You'll need to spatially join our Chipotle store locations' latitudes and longitudes onto the tigerline counties. https://geopandas.org/index.html.

Step 4. - Analysis
1. Thanks to the hard work of the authors at this link - https://ai-ml-analytics.com/multicollinearity-with-ordinary-least-squares/
we can use Ordinary Least Squares and VIF method to determine if housing prices predict physical Chipotle restaurant locations. Unfortuantely, they don't. We'll need to circle back and pick features that have fewer multicolinearities and redo our analysis. 

