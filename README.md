# Coffee During COVID-19
## Introduction

The effects of coronavirus disease 2019 (COVID-19) have impacted communities in various ways. People are now getting accustomed to new work environments that require physical distancing, some of which strictly work from home now as a potential permanent solution. These new changes are indeed making the workplace safer, but how has it impacted the social life of those who went to work every day? Social interaction may not be the first thing you think of when it comes to work but communicating with others in the workplace is something that people are used to. What will fill the void in social interaction? Going to the local coffeeshop. 

The work-at-homers now need a place to go to indulge in interacting with others. Providing a physically distanced solution for people who are yearning for caffeine, wi-fi, and the company of others is a potential business opportunity. Implementing coffee shops with an open floorplan and other amenities that facilitate both productivity and a social counterpart could be a successful venture in the decade of 2020. Now the questions are: Who would be interested in starting said coffee shops? Where does one open up a coffee shop?

Investors who are been in or outside of the coffee shop business. The interested parties who are inclined to capitalize on this business venture would be provided with potential areas of investments determined by analysis of Foursquare data. Coffeeshop “Hotspots” will be identified by analyzing the attractions around current popular coffeeshops to predict locations within Toronto where a new coffeeshop will succeed. These locations will give key insight to which sites to invest in.

## Data

Three primary data sources will be utilized in the execution of this project. Toronto postal codes, boroughs, and neighborhoods will be obtained from Wikipedia [1]. The coordinates corresponding to each postal code will be obtained from IBM [2]. Venues information will be obtained from Foursquare using a developer API call [3]. 

The postal codes and geographic coordinates will be combined to create a dataset that will allow for the venues to be found within a specified radius of the center. For each radius, venues will be counted and categorized by the “categories” section in the Foursquare data. The occurrence of each category type within a postal code will be quantified by taking the mean frequency. Assumptions of the methodology are listed below:

- A radius of 500 meters does not overlap with other postal codes
- The geographic coordinates of each postal code represent the center of the postal code

The kmeans algorithm will be employed to cluster the different postal codes based on the mean frequency of each category type within each postal code. An optimal cluster number will be found using the elbow method. A cluster number will be assigned to each postal code. The clusters that have a high frequency of coffee shops are the ones of interest. The postal codes that are within the cluster but do not have a high frequency of coffee shops will be considered to be the “hotspots” for investment. Specific examples of the data usage will be illustrated in the Jupyter notebooks associated with this repo. 

## References
[1] 	Wikipedia, "List of postal codes of Canada: M," 21 September 2020. [Online]. Available: https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M. [Accessed 22 October 2020].

[2] 	IBM, "Coordinates," [Online]. Available: https://cocl.us/Geospatial_data. [Accessed 22 October 2020].

[3] 	Foursquare, "Places Data," [Online]. Available: https://developer.foursquare.com/places. [Accessed 13 November 2020].
