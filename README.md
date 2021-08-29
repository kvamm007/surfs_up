# Surfs Up Analysis
## Overview
The purpose of this analysis of weather on the island of Oahu is to assess the viability of a surf and ice cream shop being opened on the island. Ideally, weather patterns will support the shop being open and successful year-round. To do this, we analyzed weather data from around the island of Oahu, focusing on temperatures collected and precipitation recorded, and particularly focusing in on June & December as opposite points of time in the year to try to get a better picture of year-round viability. 

## Results
Key observed differences & similarities between June & December on Oahu.

June Summary: ![June data](https://user-images.githubusercontent.com/85597801/131235013-baf4309b-01bc-4130-8675-8ab5ee981c7f.png)
December Summary:![Dec data](https://user-images.githubusercontent.com/85597801/131235015-f7ef4b6f-297d-43e3-9dcd-f77af0158df0.png)

### Similarities:
-	The max temperatures for both months are very close, indicating that regardless of time of year, it likely rarely gets above the mid-80s on Oahu
-	The standard deviations are very close in size, so June and December both have steady weather throughout the month, without large variations
-	The interquartile ranges, along with the standard deviation, are very similar (4 for June and 5 for December) further supporting the steadiness of temperatures in both months. 
### Differences:
-	June has about 12% more data points than December- it may be worth investigating why, as December actually has one day more than June, we would not expect to see such a large difference in reported temperatures
-	The mean temperature in June is approximately 4 degrees warmer than in December. Compared to our Midwest weather, that is a very small difference, however, the difference between 71 and 75 could well be the difference between being warm enough to go into the ocean and making more casual surfers hesitant to swim. 
-	The minimum temperature in December is about 8 degrees colder than in June, which is a noticeable amount; the low of 56 in December may be getting a bit chilly to enjoy an ice cream.
-	In general it appears both months have typical temperatures in the 70s, however, December temperatures tend to be mid-low 70s, while June tends to be mid-high 70s. Further analysis on the point at which desire to eat ice cream and surf based on temperature drops off may be warranted. 
## Summary
Since both months contain temperatures in the 70s, they are fairly similar. It may be warranted to perform more research, either specifically on Oahu or globally, plotting temperature against ice cream sales and number of people surfing. If 75 degrees were a tipping point on either, that may make a large difference in our sales. 
### Additional Queries for Further Analysis
-	I would recommend comparing the average rainfalls as well. People are not going to be out and about as much on rainy days, nor are they going to be as likely to want to enjoy a cold ice cream. They also may be less likely to want to surf. Queries that could accomplish this are:
```
    june_perc=session.query(Measurement.date, Measurement.prcp).\
        filter(func.strftime("%m", Measurement.date) == "06")

    dec_perc=session.query(Measurement.date, Measurement.prcp).\
        filter(func.strftime("%m", Measurement.date) == "12")
```

-	I would recommend spending some time reviewing the weather stations available. From our earlier analysis, we determined there were 9 weather stations reporting data. It may be worth while to map out their locations, and compare those to the location we plan to launch the surf shop. The Hawaiian Islands can have drastically different weather on the same day between the beach and up in the mountains; we may be getting additional precipitation and cooler temperatures by including data from weather station at high mountain altitudes, which would have no impact on our surf shop. Queries to accomplish this would be:
```
    june=session.query(Measurement.date, Measurement.tobs).\
        filter(func.strftime("%m", Measurement.date) == "06").\
		    filter(Measurement.station == '<station ID>')
```    
Fill <station ID> with the full station ID chosen to represent the closest weather station.

To switch to December (from June), change “06” to “12”.

To switch to percpitiation (from Temperature), change Measurement.tobs to Measurement.prcp.
