# Predicting Diabetes Prevalence Using Social Determinants of Health Factors

## Introduction/Rationale
Diabetes prevalence has significantly increased over the past two decades. According to the CDC's 2020 National Diabetes Statistics Report, median age-adjusted diagnosed diabetes prevalence at the county level increased from 7.8% in 2004 to 13.1% in 2016 (see graph below).

<img width="520" alt="image" src="https://github.com/user-attachments/assets/86402d48-e96f-4e38-84e9-d77ec73e7d88" />

Research suggests that Social Determinants of Health (SDoH), the non-medical factors encompassing the conditions in which people are born, grow, live, work, and age, play a powerful role in shaping health outcomes. This analysis identifies key SDoH factors that are important in predicting diabetes prevalence, which could inform targeted public health interventions and promote preventative care strategies to reduce diabetes risk.

## Data Sources
The data sources included in this project are:
  1. American Community Survey (ACS, 2021) - Survey data from 3.5 million addresses on 40+ topics conducted by the Census Bureau. Topics include age, children, veterans, commuting, education, income, and employment. The data used here are 5-year estimates. New data is available every year. Data reflects 5-year period not a point in time. Data is collected through internet, mail, and in-person visits.
  
  2. CDC Local Data for Better Health (CDC, 2021) - Estimates for 36 health measures designed to be used to identify emerging health problems and to help develop and carry out effective, targeted public health prevention activities.
  
  3. CDC Social Vulnerability Index (SVI, 2018) - Social vulnerability is the degree to which a community exhibits certain social conditions that may affect that community's ability to prevent human suffering and financial loss in the event of a disaster. Index indicating the relative vulnerability of every U.S. ZCTA. Ranks on 5 social factors and groups them into 4 related themes.

After aggregating these datasets and ensuring high data quality, exploratory data analysis was conducted to determine which SDoH factors have the strongest relationship with diabetes prevalence. After feature selection, the model building process consisted of iterating through several ML techniques (linear regression, lasso regression, ridge regression, random forests, XGBoost, and KNN) to select model that minimizes test MSE the most.

