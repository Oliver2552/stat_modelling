# Exploring Urban Dynamics: Bike Station Proximity, Points of Interest, and Predictive Modeling in Toronto

## Project/Goals
The aim of this project was to gather data on all rental bike stations in Toronto, Ontario, Canada through the cityBike API.

More specifically, using the data on all bike stations, gather data on all bars and libraries within a 1000m (1km) radius of both POI's and investigate any potential relationships.

Next, use the data and build a statistical regression model to predict the availability of bikes, based on various POI details.

Finally, assess the quality of and interpret the model results.


## Process
### Step 1: Gather Data from CityBikes API
Here we gathered data on all rental bike stations in Toronto, Canada. More specifically, extracted from the JSON the latitude and longitude of each bike station and the availability of bikes (during time of running query). This can be seen in the 'city_bikes.ipynb' notebook in the notebooks folder.

### Step 2: Gather Data from Foursquare and Yelp API's
Here, we gathered data, based on all bike station lat/long coordinates on all bars and librarys within a 1000m (1km) radius of each bike station. We then extracted info we needed and created dataframes for later exploration.

Our method here of directly feeding in the latitutes and longitudes of each bike station (from the citybikes API) into both the YELP and Foursquare APIs ensure data integrity and data quality, with no duplicate rows. This can be seen in the 'bike_poi_radius_yelp.ipynb' and 'bike_poi_radius_fsq.ipynb' notebooks in the 'notebooks' folder.

### Step 3: EDA - Foursquare/Yelp Results Comparison
Compared both results from Foursquare and Yelp to see which was better, which provided more info/details. Ultimately Foursquare was more favourable with more datapoints and would go on to be used in model building/regression.

### Step 4: Model Building/Multiple Linear Regression/Results Interpretation
Using the DataFrame created from Foursquare results, a model was created to predict the number of free bikes, based on the number of bars and libraries local to each bike station as well as the POI with the shortest distance from each bike station.

## Results
Key findings:

- The number of bars and availability of bikes share a positive correlation
- The number of librarys and availability of bikes share an inverse relationship
- the final model had an adjusted R-squared of .116, implying that there is quite a bit of room available for further explanation in variability - more variables are needed.

## Challenges 
- YELP's API has a lower rate limit of 500 meaning we could only make 250 rows of data. we queried the Yelp api twice for every bike station, once for bars and once for libraries.


## Future Goals

- Query the YELP api over several days to feed in all 717 bike station cooridnates, for every 250 stations we made 500 calls which is the api's limit.

- Find more POI's to explore so as to improve the models adj r-squared and explainbility, .116 is quite low.

- Develop a classification model from the data gathered.
