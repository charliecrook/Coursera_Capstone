# House Prices and Common Venues in London

## Description and Discussion of the Background

London is one of the largest cities in Europe with a population of 8,908,081 and population density of 5,666/km2. The city is divided into thirty-two boroughs with the City of London making up a thirty-third borough. Each London borough has a unique demographic and an individual cultural identity. The average residential property values range from £1,294,907 in the borough of Kensington and Chelsea to £303,631 in the borough of Barking and Dagenham. This report will compare boroughs based on average residential property price and common local venues. 

The report aims to answer the question: “Can a London resident find new boroughs that share characteristics with boroughs that they already enjoy?” Consider a London resident who is looking to move to a new house. This individual may already have an idea of some potential boroughs in which they would like to live. Given the individual’s budget and venue preferences, it should be possible to identify other boroughs that share the same characteristics; the new boroughs should be sufficiently similar in residential property value and local venue types. By mapping clusters of boroughs to a chloropleth map of prices, it should be easy to visualise the similarities between boroughs.

## Data Description

This report will use data from the following sources:
* Government house price data 
⋅⋅⋅This dataset (found at https://www.gov.uk/government/publications/uk-house-price-index-england-december-2019/uk-house-price-index-england-december-2019) contains the average house price by borough for the year to December 2019. This dataset uses the UK House Price Index (UK HPI) which is calculated by the Office for National Statistics and Land & Property Services Northern Ireland. Data for the UK HPI is provided by HM Land Registry. The dataset is provided in csv format and will be loaded using Pandas.

* Foursquare venue information
⋅⋅⋅Foursquare users provide information on venues throughout London. This data is hosted by Foursquare and is retrievable through use of the Foursquare API. The required data for this project is the number of venues of a given type in a defined area within each borough.

* Wikipedia co-ordinate data
⋅⋅⋅The following Wikipedia page contains a list of co-ordinates for each London borough: https://en.wikipedia.org/wiki/List_of_London_boroughs. This website will be scraped using the Beautifulsoup package and the latitude and longitude values will be loaded into a Pandas dataframe.

* Geojson file specifying London borough borders
⋅⋅⋅In order to create a chloropleth map, a geojson file with boundary data of each London borough will be needed. A suitable geojson file is available at the following Github page: https://github.com/blackmad/neighborhoods/blob/master/london.geojson.

## Application of Data

The co-ordinate data from Wikipedia will be fed into the Foursquare API. This will return a list of the one hundred most common venues within a 1,500 metre radius of the co-ordinate of each London Borough. The k-means clustering algorithm will be used to identify clusters of boroughs that share common venues. The most common venues in each cluster will then be compared to examine the characteristics of the clusters. A short description will be assigned to each cluster.

The house prices will also be visualised and categorised into five bins which will be used to provide to label containing the house price level: low, lower medium, upper medium, high and very high.

The geojson file will provide the borough boundaries for the chloropleth map. The house price data will serve as the variable to create a chloropleth map; the darker shaded regions will represent a higher average house price. The k-means cluster datapoints will be added to the chloropleth map; each datapoint will be labelled. Each label will include: the borough name, a short description of the cluster characteristics, the three most common venues in the borough, the average house price category.

The resulting chloropleth map will serve as a tool for potential homeowner to compare how boroughs with similar common venues compare in terms of average house price. The visualisation may also provide some insight as to the relationship between each cluster and average house price.

