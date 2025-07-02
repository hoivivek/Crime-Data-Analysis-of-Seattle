# Crime Data Analysis of Seattle


## Project Overview
This project provides a detailed analysis of various crimes in Seattle between 2008 and 2024. It goes beyond basic crime trends by incorporating socio-economic data, specifically poverty statistics, to investigate connections between crime rates and economic disparities. The primary goal is to identify crime patterns across neighborhoods and determine if socio-economic factors like poverty are linked to higher crime rates. The findings aim to offer actionable insights for law enforcement and community organizations to develop targeted strategies for crime prevention. 



## Methodologies

### Data Collection
Data for this project was sourced from reliable repositories:


* SPD Crime Data: Obtained from the Seattle Police Department. 


* Census Blocks Data: Collected from the U.S. Census Bureau and local sources. 


* Poverty Data: Retrieved from local government and census repositories. 


* Community Reporting Areas (CRA): Acquired from Seattle's geographic data portal. 

### Data Preprocessing

The collected datasets underwent extensive cleaning and transformation:

Seattle Police Department (SPD) Crime Data:

* Approximately 1,152,608 records detailing crime incidents. 

* Removed unnecessary columns (e.g., 100 Block Address). 

* Standardized 

* Offense Start Date Time and extracted Offense Start Date and Offense Start Time for temporal analysis. 

* Addressed data collection errors by removing records associated with non-precinct entities (OOJ, Northgate, Unknown) and corrected 'w' to 'W' for precinct consistency. 


Census Blocks Data:

* 10,293 records providing geographic and demographic information. 

* Removed irrelevant columns (e.g., Gross Acres, Land Acres, Water Acres, Council District). 


Poverty Data:

* 2,276 records offering insights into population and poverty levels. 

* Removed age-specific poverty breakdowns and other redundant fields. 


Community Reporting Areas (CRA) Dataset:

* 53 records defining community-level administrative boundaries. 

* Removed unnecessary columns (e.g., water, Area Acres, Area Square Miles). 

* CRA ID for consistency across datasets. 


### Data Merging

The data merging process integrated crime records with geographic datasets using GeoJSON files for spatial and statistical analysis. 

Crime data columns were renamed for consistency and a report number helper column was created. 

Latitude and longitude coordinates were converted into geometry points and transformed into a Geodata Frame with the EPSG:4326 Coordinate Reference System. 

The processed Geodata Frame was exported as a GeoJSON file. 

GeoJSON datasets for Census Blocks, Community Reporting Areas, and processed crime data were loaded into Geodata Frames. 

Crime data was merged with detailed crime records using 

report number as the common key, and redundant fields were removed. 

A spatial join associated each crime point with its corresponding census block. 

Crime data was aggregated at the census block level and then by CRA identifiers to calculate total crime counts. 

Missing values in the crime count field were filled with zeros. 

Data was aggregated at the neighborhood district level by grouping and summing total area and crime counts. 

Finalized datasets were exported as GeoJSON files for visualization and analysis. 

A choropleth map was created to display crime counts across Seattle neighborhoods, labeling the top 10 using centroids. 



### Results & Conclusion

High-crime neighborhoods like Capitol Hill, Cascade/Eastlake, and Queen Anne, along with the North Precinct, consistently report the highest crime counts, necessitating targeted law enforcement and community interventions. Property crimes, especially larceny-theft, are the most frequent. Peak crime hours at midnight emphasize the need for increased patrols and preventive measures during late-night hours. While a small portion of Seattle's population lives below the poverty line, the project highlights that factors beyond poverty, such as urban density and commercial activity, also drive crime rates in affluent areas. Therefore, solutions should integrate law enforcement efforts with socio-economic development initiatives like affordable housing and job creation, complemented by data-driven policing techniques, to foster safer and more inclusive communities. 





### Technologies & Libraries Used

* Python: The primary programming language for data analysis and visualization.

* Pandas: For data manipulation and analysis.

* NumPy: For numerical operations.

* Matplotlib: For creating static, interactive, and animated visualizations.

* GeoPandas: For working with geospatial data.

* Shapely: For geometric objects.

* Fiona: For reading and writing spatial data.

* GeoJSON: For encoding geographic data structures.
