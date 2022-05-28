# Forecasting the Correlation(s) between COVID-19 Cases and Housing Data

### Data Source:
- COVID-19 Data: https://healthdata.gov/dataset/United-States-COVID-19-Cases-and-Deaths-by-State-o/hiyb-zgc2
- Housing Data: https://www.kaggle.com/code/thuynyle/hawai-i-s-housing-market-post-covid/data
- Obtained US State and state abbreviation dataset from [scottechnology.com/list_of_50_state](https://scottontechnology.com/alphabetical-50-us-states-abbreviations-list/)


#### SQL Database
- We will be using SQL Database for this project (see screenshot below)
- ![Database Screenshot Week 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_%26_HOUSING_DATABASE.png)


### Data Cleaning-SQL:
- Dropping Fips column from the C dataset
- Creating a combined key to join tables using county/state from covid dataset
- Using the housing dataset, we have dropped years before 2020 in the spreadsheet to make it easier
- We split the remaning housing data into four spreadsheets two each for 2020 and 2021, so that queries run more effeciently (less columns to go through)
- We will drop uncessary columns from the housing dataset

### Reasons why we selected the topic:
 -  There is a perception that COVID-19 had immensely effected the housing market all over the United States, our project will discover if that anology is correct and their correlation
 -  Given historical data, we want to predict future COVID-19 cases and housing prices for 2022
 
### Questions we hope to answer:
- What is the relationship between COVID-19 cases and the Housing Market by a selection of States (CA, WA, TX, FL, MN) 
-

### Machine Learning Model:
- Using Python and Jupyter Notebook for learning model
- Regression or Unsupervised machine learning
- Inputs: TBD
- Output/Target: Number of positive COVID cases and housing prices in a county/state
- Output/Target: To determine if house prices increased or decreased as the covid cases increased or decreased

### Data visualization tools
- Tableau will be used to create data vizualizations

### Presentation Link
https://docs.google.com/presentation/d/1bv3LSd37Qxwq-3BTp1zodWL7fH8tMsefu9D7WUe0sQY/edit?usp=sharing

### Team Communication Protocals
- Slack channel for team members
- Zoom for live collaboration
- Tues/Thurs during class time
- Additional time as scheduled

