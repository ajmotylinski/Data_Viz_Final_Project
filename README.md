# Forecasting the Correlation(s) between COVID-19 Cases and Housing Prices for 2022

### Data Source:
- Using Covid Dataset from https://github.com/nytimes/covid-19-data
- Tables used for this project: us-counties-2020.csv, us-counties-2021.csv and us-counties-2022 files
- Using Housing Dataset from Kaggle https://www.kaggle.com/code/thuynyle/hawai-i-s-housing-market-post-covid/data
- Obtained US State and state abbreviation dataset from Social Security Administration website (https://www.ssa.gov/international/coc-docs/states.html)
- We will be using SQL Database for this project (see screenshot below)

#### Database Screenshot
![Database Screenshot.png]https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Database%20Screenshot%20(Week%201).png)

### Web Scrapping:
- Used web scrapping technique to get data from the US Social Security Administration website (https://www.ssa.gov/international/coc-docs/states.html) to create code
- table for US-State and abbreviation

### Data Cleansing:
- Dropping Fips column from the covid dataset
- Creating a combined key to join tables using county/state from covid datasets
- Using the housing dataset, we have dropped years before 2020 in the spreadsheet to make it easier
- We split the remaning housing data into four spreadsheets two each for 2020 and 2021, so that queries run more effeciently (less columns to go through)
- We will drop uncessary columns from the housing dataset

### Reasons why we selected the topic:
 -  COVID is something that affects everyone
 -  Given historical data, we want to predict future COVID-19 cases and housing prices for 2022
 
### Questions we hope to answer:
- What will be the covid cases for 2022 by County and State?
- Discover Covid 19 trends across multiple years

### Machine Learning Model:
- Using Python and Jupyter Notebook for learning model
- Regression or Unsupervised machine learning
- Inputs: TBD
- Output/Target: Number of positive COVID cases and housing prices in a county/state
- Output/Target: To determine if house prices increased or decreased as the covid cases increased or decreased

### Data visualization tools
- Tableau will be used to create vizualizations

### Team Communication Protocals
- Slack channel for team members
- Zoom for live collaboration
- Tues/Thurs during class time
- Additional time as scheduled

