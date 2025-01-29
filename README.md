# Predicting Diabetes Prevalence Using Social Determinants of Health Factors

## Introduction & Rationale
Diabetes prevalence has significantly increased over the past two decades. According to the CDC's 2020 National Diabetes Statistics Report, median age-adjusted diagnosed diabetes prevalence at the county level increased from 7.8% in 2004 to 13.1% in 2016 (see graph below).

<img width="520" alt="image" src="https://github.com/user-attachments/assets/86402d48-e96f-4e38-84e9-d77ec73e7d88" />

Research suggests that Social Determinants of Health (SDoH), the non-medical factors encompassing the conditions in which people are born, grow, live, work, and age, play a powerful role in shaping health outcomes. This analysis identifies key SDoH factors that are important in predicting diabetes prevalence, which could inform targeted public health interventions and promote preventative care strategies to reduce diabetes risk. This analysis demonstrates how machine learning techniques can be used to determine these key factors.

## Data Sources
Public SDoH data can be found at the ZCTA, county, and census tract levels. Diabetes prevalence data is available at both the census tract level and the county level. This analysis uses data at the ZCTA and census tract level. The data sources included in this project are:
  1. American Community Survey (ACS, 2021) - Survey data from 3.5 million addresses on 40+ topics conducted by the Census Bureau. Topics include age, children, veterans, commuting, education, income, and employment. The data used here are 5-year estimates. New data is available every year. Data reflects 5-year period not a point in time. Data is collected through internet, mail, and in-person visits.
  
  2. CDC Local Data for Better Health (CDC, 2021) - Estimates for 36 health measures designed to be used to identify emerging health problems and to help develop and carry out effective, targeted public health prevention activities. Diabetes prevalence data comes from this dataset.
  
  3. CDC Social Vulnerability Index (SVI, 2018) - Social vulnerability is the degree to which a community exhibits certain social conditions that may affect that community's ability to prevent human suffering and financial loss in the event of a disaster. Index indicating the relative vulnerability of every U.S. ZCTA. Ranks on 5 social factors and groups them into 4 related themes.

## Methodology
This analysis features data extract, data preprocessing, exploratory data analysis, feature selection, model building, and model selection procedures.

### Data Extraction & Data Preprocessing
The ACS data was extracted via API call to Census Bureau. Both the CDC and SVI data were imported via an excel file downleaded from the CDC's website. ZCTA to zip code and census tract to zip code mappings were used to aggregate ZCTA-level and tract-level data to the zip code-level.

### Exploratory Data Analysis
Initial assessments were conducted to understand the data structure and the number of missing observations. A univariate analysis was performed on all features including calculating measures of center and spread (numeric) and frequency tables (categorical), visualizing shapes of distributions via histogram and Q-Q plot, checking normality assumptions, and detecting outliers. A bivariate analysis was also created by generating scatterplots (continuous vs. continuous) and identifying the features with the highest Pearson correlation to determine the strength and directon of the relationship between features and diabetes prevalence (continuous vs. continuous). Boxplots, violin plots, and ANOVA tests were conducted to detect relationship between continuous and categorical features. A multivariate analysis was also performed using interaction plots and iterating through several linear regression models to determine if there were any potential interactions between features. The features that appeared to have the strongest relationship with diabetes prevalence were: region, proportion of age over 64, proportion of race - White, proportion of race - Black, proportion of housing < $500 per month, proportion employed, proportion with poverty ration under 1.50, proportion with food stamps, median household income, proportion without a high school diploma, proportion with a Bachelor's degree, proportion with a Graduate's degree or higher, proportion who drives a car, truck, or van to work, proportion who works from home, and proportion without internet.

### Model Building
After dummy coding the region variable (Midwest, Northeast, South, West), the data was split into a training set (70%), a testing set (15%), and a holdout set (15%). The data was then trained on several machine learning algorithms including linear regression, lasso regression, ridge regression, elastic net regression, decision trees, random forest, XGBoost, and K-nearest neightbors. When appropriate, ensured there was no multicollinearity between features in the linear models. Hyperparameter tuning was also performed on the more advanced machine learning techniques. 

## Results & Insights
The best model was determined by having the lowest test MSE. In this case, the best model was the KNN model with the lowest normalized test MSE at 0.1991. The features included in this model are: egion, proportion of age over 64, proportion of race - White, proportion of race - Black, proportion of housing < $500 per month, proportion employed, proportion with poverty ration under 1.50, proportion with food stamps, median household income, proportion without a high school diploma, proportion with a Bachelor's degree, proportion with a Graduate's degree or higher, proportion who drives a car, truck, or van to work, proportion who works from home, and proportion without internet.

## Conclusion
This analysis not only highlightshow advanced ML techniques can use SDoH to predict diabetes prevalence but also captures the key SDoH factors that are strongly associated with diabetes prevalence. Note that as new public SDoH data is available, this model will need to be re-trained to prevent model degredation. Until new diabetes prevalence estimates are released, this model can be used to predict diabetes prevalence, which can hopefully inform targeted public health interventions and promote preventative care strategies to reduce diabetes risk.
