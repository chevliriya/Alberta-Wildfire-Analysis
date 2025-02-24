# Alberta-Wildfire-Analysis
# Group Member : Riya Chevli , Deepika Gollamandala , Yilin Wan . 
## Project Overview : 
Wildfires naturally occur in many ecosystems and play an important role in helping forests and grasslands regenerate by removing old plants. However, they can become harmful when they occur close to populated areas, where they can destroy homes, businesses, and even lead to injuries or loss of life. We chose to study wildfires because they are a complex issue with overarching and lasting impacts across the environment, ecology, and economy of communities, especially in this part of the world, as seen in the recent fires in California. News reports highlight that 2023 has been an especially severe year for wildfires in Canada. Recently, there has been a noticeable rise in both the frequency and intensity of these fires.

Alberta is no stranger to wildfires—the latest one being the devastating wildfire in Jasper during the summer of 2024, in which about 30% of the tourist town was destroyed by fire. Studying wildfires, their patterns, causes, and characteristics helps us understand them and find ways to prevent and mitigate them, keep communities safe, and protect the environment.

## Guiding questions : 
To thoroughly understand wildfires in Alberta, we formulated the following guiding questions. The insights gathered will contribute to the development of effective wildfire management strategies.
1. What are the primary causes for wildfires in Alberta?
2. Any differences in characteristics of wildfires started by natural causes vs. human activity?​
3. During which months are fires most frequent?
4. How do weather conditions affect the size and spread of wildfires?​
5. How does the type of trees affect the size and spread?
6. Any observable trends in the frequency or size of wildfires in Alberta over the years?

## Dataset : 
#### 1. Historical wildfire dataset
- Source: https://open.alberta.ca/opendata/wildfire-data
- Description: The dataset covers 17 years of wildfire data in Alberta (2006–2023). It includes details such as causes, size, location, time, duration, weather conditions, resources used, and the area burned [open.alberta.ca].
- Size: The dataset is stored in csv format and has 25322 rows and 50 variables in the dataset. 
- Format: CSV

### 2. Historical Air Quality Dataset
- source : https://data.calgary.ca/Environment/Average-Daily-Air-Parameter-Values/vi73-jiec
- Description : The dataset includes average air quality index data.
- size:The dataset is stored in csv format and has 26057 rows and 9 variables in the dataset.

## Project Implementation:
###  Part 1: Data Cleaning and Preprocessing  
  1.1  Load and Inspect the Datasets  
  - Load the dataset and display its shape, column names, and data types.
  - Identify and list the number of missing values in each column.
  - Check for duplicate rows and remove if found.
    
  1.2  Handling Missing Data  
  -  Drop columns with more than 35% missing values.
  -  We chose not to handle outliers to study the causes and characteristics of extreme fires. Missing values were filled using the K-Nearest Neighbors (KNN) algorithm, as discussed in class.
  -  Numeric columns were imputed with KNN, while missing values in categorical columns were replaced with the most frequent value.
  
### Part 2: Data Transformation and Analysis    
 2.1 Group and Aggregate:  
 - We split our data into three categories preCOVID, COVID and postCOVID and it groups the data by the general cause of the fire varaible(general_cause_desc).
 - Apply aggregate function for different varaible. Used mean and median for burned area (ex_hectares) and only mean used for fire spread rate ,temperature, relative humidity, and wind speed.
 - Create new column period which assign each row to one of three periods based on the fire_year column and group this column to ex_hectares and perform max , avg , total burned area opration.
 
 2.2 Joining Data  
 - Here we create pivot table to give us  Top 5 Most Frequent General Causes by Period.
 
### Part 3: Data Visualization
Through the line chart, it can be observed that the number of wildfires generally reaches its peak in May, while in some years, July is the peak, and the number of wildfires from November to March is very low.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Frequency%20of%20fire(2006-2023).png?raw=true)  

From the bar chart, it can be seen that May is the month with the most frequent occurrence of wildfires, with about 6000 incidents in the past 18 years. Overall, May to July is the period with the most frequent wildfires, while December to February has relatively fewer fires.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Frequency%20of%20fire.png?raw=true)  

In this bar chart shows the number of fires caused by different factors, with lightning and recreation being the main causes, followed by resident and incendiary. Agriculture, the wire industry, and other industries also contribute to the number of fires, while reasons such as railroad and government are less important.  
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/primary%20cause.png?raw=true)

In this line plot show how wildfire occurrences change by month for each cause type, highlighting trends across the year.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/natural%20vs%20human(frequency).png?raw=true)

A stacked bar chart to show the distribution of wildfire sizes for each cause type, with different colors representing size categories.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/natural%20vs%20human(size).png?raw=true)  

In this box plot compare the spread rate between different wildfire cause types. It shows the median,  spread, and potential outliers for spread rate associated with each cause type.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/natural%20vs%20human(spread%20rate).png?raw=true)

Here first filters the data to focus only on the Air Quality Index parameter from the station Calgary Central, then creates a boxplot to compare air quality levels (Average Daily Value) between different wildfire cause types (e.g., natural or human-caused). The boxplot shows the median, spread, and potential outliers for air quality values associated with each cause type.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/natural%20vs%20human(air%20quality).png?raw=true)  

The 3D scatter plot illustrates that when the temperature is between 20-30 degree Celsius, the relative humidity is between 20-40%, and the wind speed is between 10-50km/h, it is more likely to cause large-scale wildfires.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Temperature,%20Humidity,%20and%20Wind%20Speed%20vs%20Fire%20Size.png?raw=true)  

The 3D scatter plot illustrates that when the temperature ranges between 10-30°C, relative humidity is between 20-60%, and wind speed falls between 0-40 km/h, the fire spread rate is notably higher, highlighting the combined influence of these environmental factors on wildfire behavior.   
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Temperature,%20Humidity,%20and%20Wind%20Speed%20vs%20Fire%20Spread%20Rate.png?raw=true)   

The bar graph compares the average air quality index (Average Daily Value) between fire days and non-fire days, with blue bars representing non-fire days and red bars representing fire days. The graph visually shows how the air quality differs between these two conditions, and the values are labeled above each bar for clarity.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/non-fire%20day%20and%20fire%20day(air%20quality).png?raw=true)  

The scatter plot shows the relationship between wind speed and temperature for different fire classes, with each point representing a wildfire. It uses color to distinguish between fire classes (ranging from minimal to extensive impact), allowing us to see how temperature and wind speed influence the fire's severity.  
- The second graph is similar but includes all fire classes, not just the large and extensive impact fires, providing a broader view of the data.
- The scatter plot reveals that most large impact fires occur when the temperature is between 20 and 30°C and wind speed is between 0 and 40 km/h, highlighting the critical environmental conditions that contribute to the severity of these fires.

![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Temperature%20and%20wind%20speed%20on%20fire%20class%202.png?raw=true)   
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Temperature%20and%20wind%20speed%20on%20fire%20class.png?raw=true)  

The bar chart shows the distribution of wildfires based on different vegetation types (fuel types), with each bar representing the number of fires associated with each vegetation type. The x-axis displays the fuel types, while the y-axis shows the number of fires, and the chart helps identify which vegetation types are most commonly associated with wildfires.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/distribution%20of%20wildfire%20by%20vegetation%20type.png?raw=true)  

The bar chart displays the average fire spread rate for different vegetation types (fuel types), with the bars representing the average spread rate (in meters per minute) for each vegetation type.   
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/avg%20fire%20spread%20rate%20by%20vegetation%20type.png?raw=true)   

The line chart shows the yearly trend of wildfires in Alberta, with the x-axis representing the years and the y-axis representing the number of fires each year. The red line with circular markers highlights how the number of wildfires has varied over the years, helping to identify periods with higher or lower wildfire activity. The x-axis is limited from 2006 to 2023, providing a clear view of the fire trends within this range.  
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/yearly%20trend%20of%20wild%20fire%20.png?raw=true)  

The line chart shows the yearly trend of the total area burned in wildfires across Alberta, with the x-axis representing the years and the y-axis showing the area burned (in million hectares). The green line with circular markers highlights how the area affected by wildfires has changed over the years, with peaks and valleys indicating periods of higher or lower fire activity. The chart is focused on the years from 2006 to 2023, providing a clear view of the trends in wildfire size during this period.  
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/yearly%20trend%20of%20area%20burnt.png?raw=true)   

### Comparision Of Three Period Analysis :   
This bar chart displays the average fire size (in hectares) for each period (Pre-COVID, During-COVID, and Post-COVID), with the height of each bar representing the average size of wildfires during that specific period. 
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Avg%20fire%20size%20during%20period.png?raw=true)  

The group bar chart shows counts fire causes for each period and show how the number of fires for each cause changes across different periods using shades of red.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/distribution%20of%20fire.png?raw=true)   

This bar chart compares the top 5 wildfire causes across periods (precovid, covid, postcovid) and showing the number of cases for each cause in each period using different colors.  
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/most%205%20frequent.png?raw=true)  

This pie chart shows the distribution of the total area burned across different periods (Pre-COVID, During-COVID, and Post-COVID), with each slice representing the proportion of the total area burned in that period.  
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/distribution%20area%20burnt.png?raw=true)  


 
### Part 4: Further Analysis  
  4.1  Correlation Analysis   
  - Here we perform correlation analysis during different period.
 - Here calculates the correlation matrix for wildfire-related variables to measure how strongly they are related (correlation coefficients range from -1 to 1). 

- Numbers and colors indicate the strength and direction of the relationships (e.g., darker orange means stronger positive correlation, while lighter shades or negative values indicate weaker or negative correlations).The diagonal values are always 1.0 since a variable is perfectly correlated with itself.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/correlation%20by%20period.png?raw=true)
    
  4.2  Hypothesis Testing  
  - We conducted hypothesis testing to compare three periods: pre-COVID, during COVID, and post-COVID. The results led us to reject the null hypothesis, indicating a significant difference in the mean burned area across these periods.
  
### Part 5:  Conclusions and suggestion   

##### (1) Fire Occurrence:
- Most fires occur during the month of May, with summer months (May to August) seeing highest  number of fires
    
##### (2) Causes of Fire: 
- Lightening is the leading cause of fires, followed by recreation activity.
    
##### (3) Differences in Fire Characteristics:
- Yes, there are differences in the characteristics of natural fires and human made fires. 
- Fires due to human activity-  spread through out the year while the fires due to natural causes are seasonal and restricted to the summer months.
- The natural fires spread faster and can cause extensive damage in a short period. Also, they have immediate affect on the air quality

##### (4) Weather Conditions:
- Temperature – Most number of fires occur when the temperature is between 10-30 c
- Windspeed – Most number of fires occur when the  wind speed is in the range 0-40 kms/hr
- Humidity – Most number of fires occur when  the relative humidity is 10-40% 

##### (5) Fire Spread rate:
- Fire spreads fastest  when  Temp - 10-30 C, relative humidity- 10-40 % and wind speed is 0-40 km/hr


##### (6) Impact of wildfires on air quality index.
- Air quality index is lower on the days with no fires, indicating better air quality.
 
 
##### (7) Impact of Vegetation
- Coniferous forests, followed by grasslands are more fire-prone. These tree types burn faster –they have higher fire spread rate. 

##### (8) Overall trends in frequency and size:
- There is a downward trend in number of fires since 2015. The trend in size of fire seems to be cyclical. 
- In 2023 2M hectares of  area got burnt in Alberta. This is equivalent to 24 times the size of Calgary


##### (9) Comparison of fires in Pre-covid, covid and Post-covid period
- The average fire size is greatest in the post covid period. This is because the period saw some of most largest fires in the recent times.
- The post covid period(2 years) accounts for about 40% percent of the area that got burnt during the last 18 years.

#### Suggestions

To Reduce Frequency and Impact of Forest Fires:

- Implement stricter regulations and monitoring during high-risk months.
- Increase public awareness and education on fire prevention, especially related to recreational activities.
- Enhance early detection and rapid response systems for natural fires.
- Improve forest management practices to reduce fuel load and fire-prone vegetation

##  Tools & Technologies  
- Python (pandas, numpy, scikit-learn)
- Jupyter Notebooks for code and report
- Data visualization libraries (matplotlib, seaborn,plotly)
- Version control: GitHub
  
