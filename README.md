# Impact of Health Factors on Diabetes

## Rose Birkner, Owen Senn

#### Data Description

The data set for this project came from kaggle here: <https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset/data?select=diabetes_012_health_indicators_BRFSS2015.csv>. That is a cleaned version of a data set which came from another kaggle project here: <https://www.kaggle.com/datasets/cdc/behavioral-risk-factor-surveillance-system?select=2015.csv>. This data comes from the Behavioral Risk Factor Surveillance System (BRFSS), an annual phone survey conducted by the CDC. Every year the data is collected from over 400,000 adults across America. The purpose of the survey is to collect information on possible health indicators of several chronic diseases as well as to record general health trends. During the survey, 330 variables are recorded. Among the information gathered is demographics, physical activity level, diet, chronic diseases, and more. Our focus for this project is looking at Diabetes and the related health factors that might indicate the occurance of it.

Due to the large number of variables and observations, the original data set would have been impractical to use and unmanageable. Additionally, because the survey records such a wide variety of information it was unnecessary to look at variables that weren't related to the focus of our project, diabetes. For these reasons we used the more selective dataset on kaggle, which was much more manageable and included the variables necessary to look at diabetes and the health factors that might influence it. On the kaggle project there were three csv files. We chose to use the file with over 250,000 observations, a variable that recorded whether someone was diabetic, prediabetic, or had no diabetes, and 21 other variables. This particular dataset was from the BRFSS survey conducted in 2015.

#### Data Cleaning

#### Variables

-   

-   

-   

-   

-   

-   

-   

-   

-   

-   

-   

-   HvyAlcoholConsump: categorical variable where 1 indicates a heavy drinker and 0 is not a heavy drinker. Heavy drinker is defined as adult men having more than 14 drinks per week and adult women having more than 7 drinks per week.

-   AnyHealthcare: categorical variable where 1 indicates having any kind of health care coverage and 0 is no healthcare coverage.

-   NoDocbcCost: categorical variable. 1 = yes and 0 = no in response to the question "Was there a time in the past 12 months when you needed to see a doctor but could not because of cost?"

-   GenHlth: categorical variable with 5 levels that indicates general health. 1 = excellent, 2 = very good, 3 = good, 4 = fair, 5 = poor.

-   MentHlth: numerical variable that indicates the number of days in the last 30 days that the participant's mental health was not good.

-   PhysHlth: numerical variable that indicates the number of days in the last 30 days that the participant's physical health was not good.

-   DiffWalk: categorical variable. 1 = yes and 0 = no in response to the question "Do you have serious difficulty walking or climbing stairs?"

-   Sex: categorical variable. 0 = female, 1 = male.

-   Age: categorical variable with 13 levels that indicate the age range of the participant. 1 = 18-24, 2 = 25-29, 3 = 30-34, 4 = 35-39, 5 = 40-44, 6 = 45-49, 7 = 50-54, 8 = 55-59, 9 = 60-64, 10 = 65-69, 11 = 70-74, 12 = 75-79, 13 = 80 or older.

-   Education: categorical variable with 6 levels that indicates education levle. 1 = never attended or only kindergarten, 2 = grades 1-8 (Elementary), 3 = grades 9-11 (some high school), 4 = grade 12 or GED (high school graduate), 5 = college 1-3 years (some college or technical school), 6 = college 4 years or more (college graduate).

-   Income: categorical variable with 8 levels that indicate income level. 1 = less than \$10,000, 2 = less than \$15,000, 3 = less than \$20,000, 4 = less than \$25,000, 5 = less than \$35,000, 6 = less than \$50,000, 7 = less than \$75,000, 8 = \$75,000 or more

#### Questions to be addressed

-   How does smoking and alcohol affect an individuals chances to have diabetes?
-   Is there a relationship between heart disease/attack or stroke and diabetes? Does this differ between men and women?
