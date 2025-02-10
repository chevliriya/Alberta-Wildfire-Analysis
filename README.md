# Alberta-Wildfire-Analysis
# Group Member : Riya Chevli , Deepika Gollamandala , Yilin Wan . 
## Project Overview : 
Wildfires naturally occur in many ecosystems and play an important role in helping forests and grasslands regenerate by removing old plants. However, they can become harmful when they occur close to populated areas, where they can destroy homes, businesses, and even lead to injuries or loss of life. We chose to study wildfires because they are a complex issue with overarching and lasting impacts across the environment, ecology, and economy of communities, especially in this part of the world, as seen in the recent fires in California. News reports highlight that 2023 has been an especially severe year for wildfires in Canada. Recently, there has been a noticeable rise in both the frequency and intensity of these fires. We aim to explore the underlying causes driving this trend.

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
Description: The dataset covers 17 years of wildfire data in Alberta (2006–2023). It includes details such as causes, size, location, time, duration, weather conditions, resources used, and the area burned [open.alberta.ca].
Size: The dataset is stored in csv format and has 25322 rows and 50 variables in the dataset. 
Format: CSV

### 2. Historical Air Quality Dataset
source : https://data.calgary.ca/Environment/Average-Daily-Air-Parameter-Values/vi73-jiec
Description : The dataset includes average air quality index data.
size:The dataset is stored in csv format and has 26057 rows and 9 variables in the dataset.

## Project Implementation:
### Part 1: Data Cleaning and Preprocessing  
  1.1  Load and Inspect the Dataset
     - Load the dataset and display its shape, column names, and data types.
     - Identify and list the number of missing values in each column.
  1.2  Handling Missing Data
    - Drop columns with more than 35% missing values.
    - We chose not to handle outliers to study the causes and characteristics of extreme fires. Missing values were filled using the K-Nearest Neighbors (KNN) algorithm, as discussed in class.
    - Numeric columns were imputed with KNN, while missing values in categorical columns were replaced with the most frequent value.
  
### Part 2: Data Transformation and Analysis
### Part 3: Data Visualization
### Part 4: Further Analysis  
  4.1  Correlation Analysis
  4.2  Hypothesis Testing  
  - We conducted hypothesis testing to compare three periods: pre-COVID, during COVID, and post-COVID. The results led us to reject the null hypothesis, indicating a significant difference in the mean burned area across these periods.
### Part 5: Reporting and Insights   
We compiled our report using Python in Jupyter Notebook, providing an in-depth analysis of all insights. Each finding is supported by detailed visualizations to illustrate every possible trend and relationship clearly. Finally, the report concludes with actionable recommendations on reducing wildfires based on the analyzed data.
