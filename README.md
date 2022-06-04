# Analyzing the Relationships Between COVID-19 and Housing Data

### Presentation Link
[Google Slides Here](https://docs.google.com/presentation/d/1bv3LSd37Qxwq-3BTp1zodWL7fH8tMsefu9D7WUe0sQY/edit?usp=sharing)

### Data Source:
- COVID-19 Data: https://healthdata.gov/dataset/United-States-COVID-19-Cases-and-Deaths-by-State-o/hiyb-zgc2
- Housing Data: https://www.kaggle.com/code/thuynyle/hawai-i-s-housing-market-post-covid/data
- Obtained US State and state abbreviation dataset from [scottechnology.com/list_of_50_state](https://scottontechnology.com/alphabetical-50-us-states-abbreviations-list/)


#### SQL Database
- We will be using SQL Database for this project (see screenshot below)
- ![Database Screenshot Week 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_%26_HOUSING_DATABASE.png)

### Data Cleaning and Preprocessing-SQL: 
#### Data Cleaned, but Not Used
-  We originally cleaned a couple datasets from https://github.com/nytimes/covid-19-data before realizing the data was cumulative and didn't meet our needs
-  We did not include the details of the data cleaning for this in the readme as we did not use this in our code, but the details are included on SQL for Table Creations and SQL for Table Creations #2 in the GitHub.

#### Housing Data:
- Create Table – housing_data_2020_2021_by_state
- Table Column – period_begin_month_year
- Drop Column - County
- Table Column – period_begin_month
- Table Column – period_begin_ year
- Update/Fill period_begin_year
- Update/Fill period_begin_month
- Update/Fill period_begin_month_year
- Add Column – housing_month_year_state
- Update/Fill – housing_month_year_state
- Drop Columns - period end, period_duration, region_type, region_type_id, table_id, is_seasonally_adjusted, region, city, median_sale_price_mom, median_sale_price_yoy, median_list_price_mom, median_list_price_yoy, median_ppsf_mom, median_ppsf_yoy, median_list_ppsf_mom, median_list_ppsf_yoy, homes_sold_mom, homes_sold_yoy, pending_sales_mom, pending_sales_yoy, new_listings_mom, new_listings_yoy, inventory_mom, inventory_yoy, months_of_supply_mom, months_of_supply_yoy, median_dom_mom,	median_dom_yoy, avg_sale_to_list_mom, avg_sale_to_list_yoy, sold_above_list_mom, sold_above_list_yoy, price_drops_mom, price_drops_yoy, off_market_in_two_weeks_mom, off_market_in_two_weeks_yoy, last_updated
- Drop Columns - off_market_in_two_weeks, parent_metro_region, parent_metro_region_metro_code
- Create table – housing_data_by_state_by_month
- Drop Columns - median_sale_price, median_list_price, median_ppsf, median_list_ppsf, median_dom, avg_sale_to_list
- Add Primary Key to ‘housing_data_by_state_by_month’ Table
- Add Foreign Key to ‘housing_data_by_state_by_month’ Table
- Drop Tables - housing_data, housing_data_2020_2021_by_state

#### Covid Data:
- Create Table - covid_daily_info
- Create Table - covid_daily_info_by_month
- Extract month from submission_date as 'period_begin_month'
- Extract year from submission_date as 'period_begin_year'
- Concatenate 'period_begin_month' '-' 'period_begin_year' as 'period_begin_month_year'
- Concatenate 'period_begin_month_year' with 'state' as 'covid_month_year_state'
- Sum(new_case + pnew_case) as cases
- Sum(new_death + pnew_death) as deaths
- Filter states to MN, CA, WA, TX & FL
- Filter submission_date >= '2020-01-01' and submission_date < '2022-01-01'
- Drop Table - covid_daily_info
- Update Table Name from ‘covid_daily_info_by_month’ to ‘covid_daily_info’
- Add Primary Key to covid_daily_info
- Add Foreign Key to Add Primary Key to covid_daily_info
- Join Tables covid_daily_info and states

### Reason(s) Why We Selected the Topic:
 -  There is a perception that COVID-19 had immensely affected the housing market all over the United States, our project will discover if that analogy is correct and their correlation
 -  We want to understand how COVID-19 impacts the housing market
 
### Questions We Hope to Answer:
- What is the relationship between COVID-19 cases and the housing market by a selection of SELECTED states (CA, WA, TX, FL, MN) 

### Machine Learning Model: Unsupervised 
- Using Jupyter Notebook to connect to the SQL database
- Using Clustering (k-means) as the unsupervised machine learning model. This model was chosen to help identify how the data is clustered together. 
  - Benefits of k-means is that is it easy to use and works well on large datasets. It also works well with different shapes and sizes of clusters.
  - Limits of k-means is that the number of clusters need to be select before the model. This can be mitigated by looking at the elbow curve to determine the optimal number of clusters. Outliers could have a significant impact on the clusters.
- Inputs: COVID-19 cases, deaths and the housing data
- Output/Target: Number of COVID-19 cases and housing in the selected states
- Output/Target: To determine if house prices decreased as the COVID-19 cases increased or decreased

### Data Visualization Tool: Tableau
- We used Tableau to create the Dashboard
- We added an interactive filter for state on the dashboard. The dashboard can display information for all states (MN, FL, TX, CA, WA) or any combination of them.
- An action filter was also added to both the pie chart and the bar graph. If you select a single state on either of these the dashboard filters to show the details for that state.
 ![Tableau Dashboard 1.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_Cases_Screenshot_1.png)
 ![Tableau Dashboard 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_Case_Screenshot_2.png)


### Team Communication Protocols:
- Slack channel for team members
- Zoom for live collaboration
- Tues/Thurs during class time
- Additional time as scheduled

