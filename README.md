# Analyzing the Relationships between COVID-19 and Housing Data

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
-  We originally cleaned a couple datasets from https://github.com/nytimes/covid-19-data before realizing the data was cummulative and didn't meet our needs
#### Housing Data
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
- Drop Columns - 
- DROP COLUMN	period_end, period_duration, region_type, region_type_id, table_id, is_seasonally_adjusted, region, city, median_sale_price_mom, median_sale_price_yoy, median_list_price_mom, median_list_price_yoy, median_ppsf_mom, median_ppsf_yoy,	median_list_ppsf_mom, median_list_ppsf_yoy, homes_sold_mom, homes_sold_yoy, pending_sales_mom, pending_sales_yoy, new_listings_mom, new_listings_yoy, inventory_mom, inventory_yoy, months_of_supply_mom, months_of_supply_yoy,	median_dom_mom,	median_dom_yoy, avg_sale_to_list_mom, avg_sale_to_list_yoy, sold_above_list_mom, sold_above_list_yoy, price_drops_mom,	price_drops_yoy, off_market_in_two_weeks_mom, off_market_in_two_weeks_yoy, last_updated
- Drop Columns - off_market_in_two_weeks, parent_metro_region,	parent_metro_region_metro_code
- Create table – housing_data_by_state_by_month
- Drop Columns - median_sale_price, median_list_price, median_ppsf,	median_list_ppsf,	median_dom,	avg_sale_to_list
- Add Primary Key to ‘housing_data_by_state_by_month’ Table
- Add Foreign Key to ‘housing_data_by_state_by_month’ Table
- Drop Tables - housing_data, housing_data_2020_2021_by_state





#### Covid Data

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
 ![Tableau Dashboard 1.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_CALTER TABLE housing_data_2020_2021_by_state 
DROP COLUMN	off_market_in_two_weeks,
DROP COLUMN parent_metro_region,
DROP COLUMN	parent_metro_region_metro_code;
ases_Screenshot_1.png)
 ![Tableau Dashboard 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/COVID_Case_Screenshot_2.png)


### Team Communication Protocals
- Slack channel for team members
- Zoom for live collaboration
- Tues/Thurs during class time
- Additional time as scheduled

