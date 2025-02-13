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

Here first filters the data to focus only on the Air Quality Index parameter from the station Calgary Central, then creates a boxplot to compare air quality levels (Average Daily Value) between different wildfire cause types (e.g., natural or human-caused). The boxplot shows the median, spread, and potential outliers for air quality values associated with each cause type.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/natural%20vs%20human(air%20quality).png?raw=true)  

The 3D scatter plot illustrates that when the temperature is between 20-30 degree Celsius, the relative humidity is between 20-40%, and the wind speed is between 10-50km/h, it is more likely to cause large-scale wildfires.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Temperature,%20Humidity,%20and%20Wind%20Speed%20vs%20Fire%20Size.png?raw=true)  

The 3D scatter plot illustrates that when the temperature ranges between 10-30°C, relative humidity is between 20-60%, and wind speed falls between 0-40 km/h, the fire spread rate is notably higher, highlighting the combined influence of these environmental factors on wildfire behavior.   
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/Temperature,%20Humidity,%20and%20Wind%20Speed%20vs%20Fire%20Spread%20Rate.png?raw=true)   

The bar graph compares the average air quality index (Average Daily Value) between fire days and non-fire days, with blue bars representing non-fire days and red bars representing fire days. The graph visually shows how the air quality differs between these two conditions, and the values are labeled above each bar for clarity.
![image alt](https://github.com/chevliriya/Alberta-Wildfire-Analysis/blob/main/images/non-fire%20day%20and%20fire%20day(air%20quality).png?raw=true)

![image alt]

![image alt]  

 
 
 3.2 Bar charts showing the frequency of general causes of wildfires.

 3.3 Stacked bar chart and box plots showing the differences in fire spread rates among the fires due to natural causes and fires due to human activity.
 
 3.4 Scatter plots and 3D Scatter Plot showing the influence of weather conditions on the size, spread and frequency of fires.

 3.5 Bar chart showing the impact of wildfires on air quality in Calgary.
 
 3.6 Pie charts showing the proportions of various class of fire - minimal impact, moderate impact, extensive impact, etc.
 
 
### Part 4: Further Analysis  
  4.1  Correlation Analysis   
  - we Compute and visualize the correlation matrix between Average Daily Value, current_size, fire_spread_rate, temperature, relative_humidity, and wind_speed.we Identify strong correlations and explain their implications.
    
  4.2  Hypothesis Testing  
  - We conducted hypothesis testing to compare three periods: pre-COVID, during COVID, and post-COVID. The results led us to reject the null hypothesis, indicating a significant difference in the mean burned area across these periods.
### Part 5: Reporting and Insights   
- We compiled our report using Python in Jupyter Notebook, providing an in-depth analysis of all insights. Each finding is supported by detailed visualizations to illustrate the trends and relationships clearly. Finally, the report concludes with actionable recommendations on reducing wildfires based on the analyzed data.

##  Tools & Technologies  
- Python (pandas, numpy, scikit-learn)
- Jupyter Notebooks for code and report
- Data visualization libraries (matplotlib, seaborn,plotly)
- Version control: GitHub
  
