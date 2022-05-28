# Forecasting the Correlation(s) between COVID-19 Cases and Housing Data

### Presentation Link
[Google Slides Here](https://docs.google.com/presentation/d/1bv3LSd37Qxwq-3BTp1zodWL7fH8tMsefu9D7WUe0sQY/edit?usp=sharing)

### Data Source:
- COVID-19 Data: https://healthdata.gov/dataset/United-States-COVID-19-Cases-and-Deaths-by-State-o/hiyb-zgc2
- Housing Data: https://www.kaggle.com/code/thuynyle/hawai-i-s-housing-market-post-covid/data
- Obtained US State and state abbreviation dataset from [scottechnology.com/list_of_50_state](https://scottontechnology.com/alphabetical-50-us-states-abbreviations-list/)


#### SQL Database
- We will be using SQL Database for this project (see screenshot below)
- ![Database Screenshot Week 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_%26_HOUSING_DATABASE.png)

### Data Cleaning and Preprocessin-SQL: 
-  From the COVID-19 dataset we extracted the month and year from the period-begin
- 
- Dropping Fips column from the C dataset
- Creating a combined key to join tables using county/state from covid dataset
- Using the housing dataset, we have dropped years before 2020 in the spreadsheet to make it easier
- We split the remaning housing data into four spreadsheets two each for 2020 and 2021, so that queries run more effeciently (less columns to go through)
- We will drop uncessary columns from the housing dataset

### Reasons why we selected the topic:
 -  There is a perception that COVID-19 had immensely effected the housing market all over the United States, our project will discover if that anology is correct and their correlation
 -  We want to understand how COVID-19 impacts the housing market
 
### Questions we hope to answer:
- What is the relationship between COVID-19 cases and the housing market by a selection of states (CA, WA, TX, FL, MN) 

### Machine Learning Model: Unsupervised 
- Using Jupyter Notebook to connect to the SQL database
- Using Clustering (k-means) as the unsupervised machine learning model. This model was chosen to help identify how the data is clustered together. 
 - Benefits of k-means is that is it easy to use and works well on large datasets. It also works well with different shapes and sizes of clusters.
 - Limits of k-means is that the number of clusters need to be select before the model. This can be mitigated by looking at the elbow curve to determine the optimal number of clusters. Outliers could have a significant impact on the clusters.
- Inputs: COVID-19 cases, deaths and the housing data
- Output/Target: Number of COVID-19 cases and housing in the selected states
- Output/Target: To determine if house prices decreased as the COVID-19 cases increased or decreased

### Data visualization tools: Tableau
- We used Tableau to create the Dashboard
 ![Tableau Dashboard 1.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_Cases_Screenshot_1.png)
 ![Tableau Dashboard 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_Case_Screenshot_2.png)


### Team Communication Protocals
- Slack channel for team members
- Zoom for live collaboration
- Tues/Thurs during class time
- Additional time as scheduled

