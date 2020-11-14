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
- A café is different than a coffee shop

## Methodology

Venues were munged from the Foursquare dataset for each postal code. The postal codes with ten or fewer venues were filtered out because of lack of signal and were considered not investable. The frequencies of each venue category within a postal code were found by taking the mean of one hot encoding values. The number of zeros in each column and row were found. The venue category with the fewest number of zeros was coffee shops and the postal code with the fewest number of zeros was M5B.		

The Kmeans algorithm was employed to cluster the different postal codes based on the mean frequency of each category type within each postal code. Kmeans was implemented because it is an unsupervised method that is able to classify neighborhoods based on the attractions within. An optimal cluster number of seven was found by using the elbow method (see notebook for details). Cluster numbers were assigned to each postal code. 

Clusters were analyzed to see how frequent coffee shops were within each cluster. The cluster number 0 was chosen to be the one to analyzed because it had the highest frequency of coffee shops. The postal codes that were within cluster 0 but did not have a high frequency of coffee shops were considered to be the “hotspots” for investment. Additionally, a Folium map was utilized to depict the physical location of each postal code within cluster 0.

Details of this methodology are within the “Munging” notebook in the “notebooks” directory within this repo.

## Results
Table 1 below depicts the recommended postal codes within Toronto, CA to invest in.
Table 1: Recommended Postal Codes for Investment
| Postal Code | Coffee Shop Frequency | Most Popular Venue |
|:-----------:|:---------------------:|:------------------:|
|     M2N     |        0.060606       |      Starbucks     |
|     M5C     |        0.070588       |    Versus Coffee   |
|     M5H     |        0.080000       |      Starbucks     |
|     M4M     |        0.081081       |       Te Aro       |
|     M5B     |        0.090000       |      Starbucks     |

It is recommended to invest in something different than the most popular venue for diversification purposes. A full table of postal codes are shown in the “Munging” notebook which include neighborhood information. Postal codes within cluster 0 are displayed in an interactive Folium map located within the “plots” directory. 

Table 2 below depicts the most popular venues within cluster 0.
Table 2: Popular Venues within Cluster 0
|            Postal Code            | Coffee Shop Frequency |
|:---------------------------------:|:---------------------:|
|             Starbucks             |         0.3940        |
|            Tim Hortons            |         0.1296        |
|       Pilot Coffee Roasters       |         0.0459        |
| Everyday Gourmet (Teas & Coffees) |         0.0275        |
|      Dineen @ Commerce Court      |         0.0273        |

It is apparent that Starbucks and Tim Hortons are the top contenders for the coffee shop market. As shown in Table 1, it may not be the case for each postal code.

## Discussion

It is recommended to invest in the postal codes that have the highest frequency of coffee shops but low frequency within. The most frequent venues within the cluster are good starting points on what specific coffee shop to invest in. However, it is best to investigate these on a case-by-case basis to evaluate each of their business models. Each coffee shop venue brand may have different profitability metrics which would lead to different outcomes. 

After examining the Folium map, some of the investable postal codes are not contained within the downtown area. These locations are opportunities to explore if coffee shops would be beneficial to invest in. They may also have a lower up-front investment cost regarding property because it is away from the downtown area. On the other hand, the locations that are close to the downtown area may be a better choice to invest in because of the increased foot traffic.  

## Conclusion & Further Work

It is recommended that coffee shop investment opportunities should be explored within postal codes M2N, M5C, M5H, M4M, and M5B. Starbucks and Tim Hortons are good franchising options, but other venue types should be considered for diversification purposes. Each postal code and investment opportunity should be evaluated on a case-by-case basis. Further work in continuation of this project includes (but not limited to) the following:

-	Obtain specific location data within postal codes regarding commercial real estate availability
-	Acquire profitability metrics regarding franchises to simulate profit under different scenarios, including the commercial real estate costs
-	Verify accurate radii for each postal code to ensure all venues are accounted for; perhaps come up with a way to change to a rectangle rather than a circle to reflect the shape of the postal codes

This type of analysis is repeatable for different locations and venues. It shows potential to impact how modern-day investment decisions are made. In conclusion, this analysis is a great starting point for any potential investor to use for differing locations and venue types. 

## References

[1] 	Wikipedia, "List of postal codes of Canada: M," 21 September 2020. [Online]. Available: https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M. [Accessed 22 October 2020].

[2] 	IBM, "Coordinates," [Online]. Available: https://cocl.us/Geospatial_data. [Accessed 22 October 2020].

[3] 	Foursquare, "Places Data," [Online]. Available: https://developer.foursquare.com/places. [Accessed 13 November 2020].


