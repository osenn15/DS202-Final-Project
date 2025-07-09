# Impact of Health Factors on Diabetes

## Rose Birkner, Owen Senn

#### Data Description

The data set for this project came from kaggle here: <https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset/data?select=diabetes_012_health_indicators_BRFSS2015.csv>. That is a cleaned version of a data set which came from another kaggle project here: <https://www.kaggle.com/datasets/cdc/behavioral-risk-factor-surveillance-system?select=2015.csv>. This data comes from the Behavioral Risk Factor Surveillance System (BRFSS), an annual phone survey conducted by the CDC. Every year the data is collected from over 400,000 adults across America. The purpose of the survey is to collect information on possible health indicators of several chronic diseases as well as to record general health trends. During the survey, 330 variables are recorded. Among the information gathered is demographics, physical activity level, diet, chronic diseases, and more. Our focus for this project is looking at Diabetes and the related health factors that might indicate the occurrence of it.

Due to the large number of variables and observations, the original data set would have been impractical to use and unmanageable. Additionally, because the survey records such a wide variety of information it was unnecessary to look at variables that weren't related to the focus of our project, diabetes. For these reasons we used the more selective dataset on kaggle, which was much more manageable and included the variables necessary to look at diabetes and the health factors that might influence it. On the kaggle project there were three csv files. We chose to use the file with over 250,000 observations, a variable that recorded whether someone was diabetic, prediabetic, or had no diabetes, and 21 other variables. This particular dataset was from the BRFSS survey conducted in 2015.

#### Data Cleaning

The data set we are using was previously cleaned by Alex Teboul on Kaggle with the notebook found here: <https://www.kaggle.com/code/alexteboul/diabetes-health-indicators-dataset-notebook>. He compacted the data from the original 330 columns to the 22 we have now. This cleaning renamed columns for readability, removed instances with NA values, and cleaned up values to have 0 = no and 1 = yes for binary variables.

All of the categorical variables were of numeric type, so we changed them all to be factors. In addition, we wanted to combine the Fruits and Veggies column so that we could look at one variable that reflected diet. We called this column Fruits_and_Veggies and gave it 3 levels, 2 for an individual that said they eat both fruits and vegetables, 1 for an individual that eats either fruits or vegetables but not both, and 0 for someone that says they eat neither. The code for those modifications is below.

```{r}
library(tidyverse)

health_data <- read.csv("C:\\Users\\rosee\\OneDrive\\Documents\\Iowa State\\DS 2020\\final project\\DS202-Final-Project\\HealthFactor.csv")

#make categorical variables of type factor
health_data <- health_data %>% 
  mutate(
    Diabetes_012 = as.factor(Diabetes_012),
    HighBP = as.factor(HighBP),
    HighChol = as.factor(HighChol),
    CholCheck = as.factor(CholCheck),
    Smoker = as.factor(Smoker),
    Stroke = as.factor(Stroke),
    HeartDiseaseorAttack = as.factor(HeartDiseaseorAttack),
    PhysActivity = as.factor(PhysActivity),
    Fruits = as.factor(Fruits),
    Veggies = as.factor(Veggies),
    HvyAlcoholConsump = as.factor(HvyAlcoholConsump),
    AnyHealthcare = as.factor(AnyHealthcare),
    NoDocbcCost = as.factor(NoDocbcCost),
    GenHlth = as.factor(GenHlth),
    DiffWalk = as.factor(DiffWalk),
    Sex = as.factor(Sex),
    Age = as.factor(Age),
    Education = as.factor(Education),
    Income = as.factor(Income)
  )
  


#add fruits_and_veggies feature
health_data <- health_data %>% mutate(
  Fruits_and_Veggies = if_else(Fruits == 1 & Veggies == 1, 2,
                               if_else(Fruits == 1 | Veggies == 1, 1, 0)),
  Fruits_and_Veggies = as.factor(Fruits_and_Veggies)
) %>% 
  relocate(
    Diabetes_012:Veggies,
    Fruits_and_Veggies
  )
```

#### Variables

-   **Diabetes_012:** categorical variable where 0 is for no diabetes or only during pregnancy, 1 is for prediabetes, and 2 is for diabetes.

-   **HighBP:** categorical variable where 0 indicates no high blood pressure and 1 indicates that an individual has been told they have high blood pressure by a doctor, nurse, or other health professional.

-   **HighChol:** categorical variable where 0 indicates no high cholesterol and 1 indicates that an individual has been told by a doctor, nurse or other health professional that their blood cholesterol is high.

-   **CholCheck:** categorical variable where 0 indicates an individual has not had a cholesterol check in the last 5 years and 1 is that they have.

-   **BMI:** numerical variable of an individual's body mass index.

-   **Smoker:** categorical variable where 0 indicates an individual has not smoked at least 100 cigarettes in their life and 1 indicates they have.

-   **Stroke:** categorical variable where 0 indicates no stroke for an individual and 1 indicates they have been told they had a stroke.

-   **HeartDiseaseorAttack:** categorical variable where 0 indicates respondents that have never reported having coronary heart disease (CHD) or myocardial infarction (MI) and 1 indicates they have.

-   **PhysActivity:** categorical variable where 0 indicates no physical activity in the last 30 days besides an individual's regular job and 1 indicates physical activity or exercise during the past 30 days other than their regular job.

-   **Fruits:** categorical variable where 0 indicates no fruits eaten during the day and 1 indicates fruit consumption one or more times per day.

-   **Veggies:** categorical variable where 0 indicates no vegetables eaten during the day and 1 indicates vegetable consumption one or more times per day.

-   **Fruits_and_Veggies:** categorical variable where 0 indicates no fruits or vegetables eaten during the day, 1 indicates eating some fruit or some vegetables every day, and 2 indicates eating both fruits and vegetables every day.

-   **HvyAlcoholConsump:** categorical variable where 1 indicates a heavy drinker and 0 is not a heavy drinker. Heavy drinker is defined as adult men having more than 14 drinks per week and adult women having more than 7 drinks per week.

-   **AnyHealthcare:** categorical variable where 1 indicates having any kind of health care coverage and 0 is no healthcare coverage.

-   **NoDocbcCost:** categorical variable. 1 = yes and 0 = no in response to the question "Was there a time in the past 12 months when you needed to see a doctor but could not because of cost?"

-   **GenHlth:** categorical variable with 5 levels that indicates general health. 1 = excellent, 2 = very good, 3 = good, 4 = fair, 5 = poor.

-   **MentHlth:** numerical variable that indicates the number of days in the last 30 days that the participant's mental health was not good.

-   **PhysHlth:** numerical variable that indicates the number of days in the last 30 days that the participant's physical health was not good.

-   **DiffWalk:** categorical variable. 1 = yes and 0 = no in response to the question "Do you have serious difficulty walking or climbing stairs?"

-   **Sex:** categorical variable. 0 = female, 1 = male.

-   **Age:** categorical variable with 13 levels that indicate the age range of the participant. 1 = 18-24, 2 = 25-29, 3 = 30-34, 4 = 35-39, 5 = 40-44, 6 = 45-49, 7 = 50-54, 8 = 55-59, 9 = 60-64, 10 = 65-69, 11 = 70-74, 12 = 75-79, 13 = 80 or older.

-   **Education:** categorical variable with 6 levels that indicates education level. 1 = never attended or only kindergarten, 2 = grades 1-8 (Elementary), 3 = grades 9-11 (some high school), 4 = grade 12 or GED (high school graduate), 5 = college 1-3 years (some college or technical school), 6 = college 4 years or more (college graduate).

-   **Income:** categorical variable with 8 levels that indicate income level. 1 = less than \$10,000, 2 = less than \$15,000, 3 = less than \$20,000, 4 = less than \$25,000, 5 = less than \$35,000, 6 = less than \$50,000, 7 = less than \$75,000, 8 = \$75,000 or more

#### Questions to be addressed

-   How does smoking and alcohol affect an individuals chances to have diabetes?
-   Is there a relationship between heart disease/attack or stroke and diabetes? Does this differ between men and women?
-   How do physical activity and diet (eating fruits and vegetables) affect the likelihood of getting diabetes? Is one significantly more influential than the other?
-   What is the relationship between mental health and diabetes? Is poor mental health associated with poor physical activity levels and/or diet which in turn affects the occurrence of diabetes?

## Results

```{r}
health_data <- read.csv("HealthFactor.csv")
library(tidyverse)
library(ggplot2)
```

#### How do physical activity and diet (eating fruits and vegetables) affect the likelihood of getting diabetes? Is one significantly more influential than the other?

For this question we wanted to look at how diet and physical activity affect the rates of diabetes and whether prioritizing one over the other leads to different chances of getting diabetes. In this survey the only features that pertain to diet are the variables Fruits and Veggies. Recall from the description of these variables that they are both categorical with 0 indicating no fruits or vegetables eaten during the day and 1 indicating fruit or vegetable consumption one or more times per day. As stated in the data cleaning section, we thought it would be interesting to combine these two variables so we could easily compare those who eat both fruits and vegetables at least once per day to those that only prioritize eating one as well as those who eat neither fruits nor vegetables. The details of how we defined this variable are in the data cleaning section. When diet is mentioned we are referring to the variable Fruits_and_Vegetables.

This first graphic is a look at basic fruit consumption and diabetes as well basic vegetable consumption and diabetes

```{r}
health_data %>% ggplot(aes(x = Fruits, fill = Diabetes_012)) +
  geom_bar() +
  scale_fill_manual(
    values = c("#66C2A5", "#8DA0CB","#FC8D62"),
    labels = c("0" = "Not Diabetic", "1" = "Prediabetic", "2" = "Diabetic")
  ) +
  labs(title = "Fruit and Diabetes status",
       x = "Level of fruit consumption", 
       y = "count", 
       fill = "Diabetes status")

       
health_data %>% ggplot(aes(x = Veggies, fill = Diabetes_012)) +
  geom_bar() +
  scale_fill_manual(
    values = c("#66C2A5", "#8DA0CB","#FC8D62"),
    labels = c("0" = "Not Diabetic", "1" = "Prediabetic", "2" = "Diabetic")
  ) +
  labs(title = "Vegetables and Diabetes status",
       x = "Level of veggie consumption", 
       y = "count", 
       fill = "Diabetes status")
```
