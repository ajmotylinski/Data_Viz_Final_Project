# Analyzing the Relationships Between COVID-19 and Housing Data

### Presentation Link
- [Google Slides](https://docs.google.com/presentation/d/1bv3LSd37Qxwq-3BTp1zodWL7fH8tMsefu9D7WUe0sQY/edit?usp=sharing)
### Dashboard Links
- [Data Source Dashboard](https://public.tableau.com/app/profile/april.vilmin/viz/CovidHousing/COVIDHOUSING?publish=yes)
- [Machine Learning Dashboard](https://public.tableau.com/app/profile/april.vilmin/viz/CovidHousingMachineLearning/MachineLearning?publish=yes)

### Technologies Used
![image](https://user-images.githubusercontent.com/96274446/172249658-8891490b-16d3-4b65-9738-37128116d79d.png)

# Reason(s) Why We Selected the Topic:
 -  There is a perception that COVID-19 had immensely affected the housing market all over the United States, our project will discover if that analogy is correct and their correlation
 -  We want to understand how COVID-19 impacts the housing market
 
# Questions We Hope to Answer:
- What is the relationship between COVID-19 cases and the housing market by a selection of SELECTED states (CA, WA, TX, FL, MN) 

# Data Source:
- COVID-19 Data: https://healthdata.gov/dataset/United-States-COVID-19-Cases-and-Deaths-by-State-o/hiyb-zgc2
- Housing Data: https://www.kaggle.com/code/thuynyle/hawai-i-s-housing-market-post-covid/data
- Obtained US State and state abbreviation dataset from [scottechnology.com/list_of_50_state](https://scottontechnology.com/alphabetical-50-us-states-abbreviations-list/)

# Data Exploration Phase:
- Extracted data from multiple sources
- Tranformed data into tables in pgAdmin. Creating Dataframes and merging them
- Analyzed data using different machine learing modules.

# SQL Database:
- We will be using SQL Database for this project (see screenshot below)
![Database Screenshot.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/Database%20Screenshot.png)  

## ERD
- ![erd.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/erd.png)  
- 
# Data Cleaning and Preprocessing-SQL: 
## Data Cleaned, but Not Used
-  We originally cleaned a couple datasets from https://github.com/nytimes/covid-19-data before realizing the data was cumulative and didn't meet our needs
-  We did not include the details of the data cleaning for this in the readme as we did not use this in our code, but the details are included on SQL for Table Creations and SQL for Table Creations #2 in the GitHub.

### Housing Data:
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

### Covid Data:
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

# Machine Learning Models
### Preliminary Data Preprocessing
- For data preprocessing we have two options to get the data. We have the option to connect to a Postgres DB as well as importing a CSV file. The user just needs to comment/uncomment the desired way of interacting with the data. The default code is to import a CSV that is pulling from the Resources folder. There are two dataframes that are generated: covid_df and housing_df.
#### covid_df 
- There was some data processing that was needed to make the data usable in our analysis. 
We checked for any null values and we did find some null values. We did find that 7 records have null values in our covid_df so we filled these with 0. When the dataframe was created we noticed that some fields were objects rather than numeric. We had to cast month, year, cases, and deaths as integers to confirm that they were seen as number during our analysis.
#### housing_df
- We ran a series of checks in our housing_df and found that there was not any null values. We also checked the format of each column and all columns were in the correct format.
#### Merging covid_df and housing_df
- For our machine learning we needed to add covid cases and deaths to our data. We merged our covid_df and housing_df on based a key that was generated in the postgres database. Our two datasets had some duplicate columns (e.g. month, year, state) that were replicated in the output dataframe, covid_housing_df. To handle this situation, the suffix "\_y" was added.  Using the drop function of pandas and a regex to drop all columns that contained "\_y"

## Feature Engineering and Feature Selection
#### Binning
- We used Binning as out Feature engineering tool. For the analysis around the number of monthly home sales we wanted to bin based on the quartiles of the data. We used the describe to find the bins of <20K, 20K-50K, 50K-70K, 70K+ monthly home sales. 
![bin.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/bin.png)  
- State attributes were encoded using Panda's get_dummies function.

### Split into Training and Test Sets
- The datasets was split into a training set and test set using train_test_split from sklearn using a test size of 25% and train size of 75%

## Explanation of Model Choice (Including Limitations and Benefits)
### K-Means
Using Clustering (k-means) as the unsupervised machine learning model. This model was chosen to help identify how the data is clustered together. 
  - Benefits of k-means is that is it easy to use and works well on large datasets. It also works well with different shapes and sizes of clusters.
  - Limits of k-means is that the number of clusters need to be select before the model. This can be mitigated by looking at the elbow curve to determine the optimal number of clusters. Outliers could have a significant impact on the clusters.
### Logistic Regression
Logistic Regression was used to classify the number of homes sold in a month into 1 of 4 categories
Benefits:
- Logistic regression is easy to impement. It also can be used for multiple classes.
Limitations:
- Logistic regression could be prone to overfitting if the number of feature less than observations.   
- Cannot used for non linear problems.

 
### Random Forest Classifier
Random Forest Classifier was used to classify the number of homes sold in a month into 1 of 4 categories
Benifits:
- Random Forest is a bagging algorithm and uses Ensemble Learning technique. It creates as many trees on the subset of the data and combines the output of all the trees. Thus, reduces overfitting problem in decision trees and also reduces the variance and therefore improves the accuracy.
- Random Forest can be used to solve both classification and regression problems.
- Random Forest worked well with both categorical and continues variables.
- Random Forest can automatically handle missing values.
Limitations:
- Random forest creates a lot of trees and combines their outputs. To do so, algorithm requires more computational power and resources.
- It requires more time comparitively to train as it generates a lot of trees.
Application to our project:
- With a small dataset Random Forest Classifying is helpful becuase it creates n number of trees and combines the output from those trees to address overfitting.
- Our data is categorical so it fits well with Random Forest Classifier models.

## Model Changes
- The major changes between segment 2 and 3 was that we binned the number of houses sold into 4 categories. We used the describe to determine the quartiles and then chose the edges accordingly. After we did that we were able to run our logistic regression and our random forest classifier on the dataset. We were able to get positive results with the liblinear solver which the documentation says is better with small datasets. We had planned to try out some deep learning using the Keras tuner but we had a small dataset which wouldn't be sufficient for deep learning. 
## Training
- We used the binned number of houses sold as the target. We split this into our target variable y and then removed it from our X dataframe. 
- We scaled our data after it was split into train and test sets. 
- Initial training tried the lbfgs sovler got us initial results for both Random Forest Classifier and Logistic Regression
- Further research found that libliner was a better fit for our models due to the small sample size.

## Accuracy score

### SMOTEEN Classification Report and Confusion Matrix
Using SMOTEEN to balance our data, we found prediction to be 94% with a recall of 93%. The monthly sales over 70K proved to have the lowest prediction. The recall was the worst in the bin 50K-70K.

![SMOTEEN Confusion Matrix.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/SMOTEEN%20-%20Confusion%20Matrix.png)  
![SMOTEEN Confusion Matrix.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/smoteen-CF.png) 


### SMOTE Classification Report adn Confusion Matrix
Using SMOTE to balance our data, we found prediction to be 89% with a recall of 90%. The prediction for the 50K-70K category had the worst at 50% accruacty and 33% sensitivity.

![SMOTE.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/SMOTE.png)  
![smote-CF.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/smote-cf.png)

### Random Forest Classifier Classification Report
The random forest classifier is currently our best model with overall results at 97% prediction and 97% recall. The bin of 50,001-70,000 does have a lower recall amount of 67% though. 

![Random Forest Classifier.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/Random%20Forest%20Classifier.png) 
![rfc_CF.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/rfc-CF.png) 

# Data Visualization Tool: Tableau
## Tableau Dashboard Based on CSV Files From Source
- We used Tableau to create the Dashboards
- We added  interactive filters for state and date on the dashboard. The dashboard can display information for all states (MN, FL, TX, CA, WA) or any combination of them.
- Action filters were added to both pie charts and the bar graph. If you select a single state on any of these the dashboard filters all graphs to display the details for that state.
![COVID Housing 1.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/COVID%20%26%20Housing%201.png)  
![COVID Housing 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/COVID%20%26%20Housing%202.png)  
![COVID Housing 3.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/COVID%20%26%20Housing%203.png)  
![COVID Housing 4.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/COVID%20%26%20Housing%204.png)  
![COVID Housing 5.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/COVID%20%26%20Housing%205.png) 

## Tableau Dashboard For Machine Learning
- We also chose to display our machine learning visualizations in Tableau.
![Elbow Curve.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/Elbow%20Curve.png)  
![Scatter Plot 1.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/Scatter%20Plot%201.png)  
![Scatter Plot 2.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/Scatter%20Plot%202.png)  
![Scatter Plot 3.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/Scatter%20Plot%203.png)  
![3D Scatter.png](https://github.com/ajmotylinski/Data_Viz_Final_Project/blob/main/Resources/Screenshots/3D%20Scatter.png) 



# Team Communication Protocols:
- Slack channel for team members
- Zoom for live collaboration
- Tues/Thurs during class time
- Additional time as scheduled

