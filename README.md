# exploredatainR
Exploratory data analysis in R using New York City taxi data (open data).
The final writeup still needs a final edit to cut down on the number of graphs. However I have decided to post the source code for those who might be interested.

The files uploaded are as follows:-

P4_Final_Writeup_v3.rmd
R Markdown file containing the analysis of the taxi data. This version of the project is version 3. It has been checked for typos, but it might still contain some errors. A final edit has not been done. In the final version of this code many of the grpahs will be eliminated as some do not give sufficient additional insight. They are part of the exploratory process, but not part of the final analysis.

Appendix.rmd
This file shows the data munging to get the data into a clean and consistent format for analysis.


The below two files show some of my thought processes and reasoning for using MongoDB on the backend. This was to avoid having R do some of the processing in memory.

NYCTaxi.rmd
Part of my process for this project was to utilize previous knowledge. In this case by using MongoDB to store the taxi data.
This also proved useful with the data coming in csv format and maximum sizes around 2GB. It was not possible to open these files using standard spreadsheet software. The above file shows some of my pre-processing of the data including querying the csv file directly using sqldf, connecting to a MongoDB from R via libraries such as rmongodb, mongolite and nodbi.

NYCSpatial.rmd
While it was useful to store and query data in MongoDB, I also wanted to do some of the data processing inside the database itself instead of in memory using dataframes. 
In this case it was geospatial querying. I wanted to send a dataframe of all geospatial points (longitude, latitude) to MongoDB and have it return all of the neighborhoods and boroughs where each point is located. A second option is to use Hadoop, MapReduce and MongoDB using any of the available R packages.

I think nodbi offers the greatest chance of getting MongoDB to do geospatial batch processing from R (without Hadoop/MapReduce), but it requires changes to the source code. Lucky for me it was written in C. When time permits, I will modify the code so it can handle geospatial queries (batch).
I have only now started experimenting with Hadoop. I have stated to use Hive or HiveQL. However I want to expand into other areas.

Again, the final edits are not complete and I will post a final version within the next few weeks. Final edits include both the writeup, the code and eliminating some of the graphs from the final report.
