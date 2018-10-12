# exploredatainR
Exploratory data analysis in R using New York City taxi data (open data).
The final writeup is in
 
 P4_NYC_Taxi.html - https://lhdatalab.github.io/P4_NYC_Taxi.html 
 
 
## Recommendations:

Yellow taxis dominate the sector in New York City. However, there are three possible clusters wit higher earnings where green taxis could compete with yellow taxis and possibly earn higher revenue per trip (on average $10).

1. Cluster 2 - Queens to Manhattan, Credit card, Standard rate, Street-hail, weekday trips earning median fares of $38.50.
2. Cluster 15 - Queens to Queens, Cash, Standard rate, Street-hail, weekend trips earning median fares $25.75
3. Cluster 14 - Manhattan to Brooklyn, Credit card, Standard rate, Street-hail, weekend trips with median fares $19.


Two of the three groups also bypass the JFK and Manhattan restrictions in place for the green taxi sector. To ascertain if 3. is outside of the Upper Manhattan pickup restrictions, we will have to drill down to the community level using the longitude and latitude coordinates provided.

The data actually showed an interesting, unexpected pattern of high average fare trips that are not in fact JFK-based. These are standard rate trips from Queens and are high for both cash and credit card customers serviced by the yellow taxi sector. 
The green sector can target the segment(s) in which yellow taxis make the most money.

In regards to JFK trips, it might not make sense for green taxis to target this segment as the increase in average fares is only $5-$6 than that earned from standard rate customers. They would also have the additional challenge of overcoming existing JFK street-hail regulation prohibiting them from targeting these customers.


#### R code is in P4_NYC Taxi.Rmd

R Markdown file containing the analysis of the taxi data. This is part of the exploratory process, but not part of the final analysis. This file shows the data munging to get the data into a clean and consistent format for analysis.


#### Appendix.rmd

The below two files show some of my thought processes and reasoning for using MongoDB on the backend. This was to avoid having R do some of the processing in memory.


#### NYCTaxi.rmd

Part of my process for this project was to utilize previous knowledge. In this case by using MongoDB to store the taxi data.
This also proved useful with the data coming in csv format and maximum sizes around 2GB. It was not possible to open these files using standard spreadsheet software. The above file shows some of my pre-processing of the data including querying the csv file directly using sqldf, connecting to a MongoDB from R via libraries such as rmongodb, mongolite and nodbi.


#### NYCSpatial.rmd

While it was useful to store and query data in MongoDB, I also wanted to do some of the data processing inside the database itself instead of in memory using dataframes. 
In this case it was geospatial querying. I wanted to send a dataframe of all geospatial points (longitude, latitude) to MongoDB and have it return all of the neighborhoods and boroughs where each point is located. A second option is to use Hadoop, MapReduce and MongoDB using any of the available R packages.


I think nodbi offers the greatest chance of getting MongoDB to do geospatial batch processing from R (without Hadoop/MapReduce), but it requires changes to the source code. Lucky for me it was written in C. When time permits, I will modify the code so it can handle geospatial queries (batch).
I have only now started experimenting with Hadoop. I have started to use Hive or HiveQL. However I want to expand into other areas.

#### Update: I have now worked with Hadoop, Hive and Impala (and some Spark/PySpark) for the past 11 months.
