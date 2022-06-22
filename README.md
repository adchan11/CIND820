# Applications of Supervised Machine Learning Methods for the Prediction of Myocardial Infarction Complications in Hospital Patients
Author: Adrian Chan <br>
CIND820: Big Data Analytics Project <br>
Dr. Sedef Akinli Kocak <br>

## Repository Contents
This repository contains the code required to evalute which features such as medical history, symptoms at time of addmision, and therapeutic interventions are most important in predicting myocardial infarction complications in hospital patients and develop prediction models using Random Forest, naïve Bayes, Stepwise Logistic Regression and Neural Network methods.

### Report from the Canadian Chronic Disease Surveillance System: Heart Disease in Canada, 2018: 
![Heart_Disease_Map](https://www.canada.ca/content/dam/phac-aspc/images/services/publications/diseases-conditions/report-heart-disease-canada-2018/fig13-eng.jpg)<br>
 Reference: https://www.canada.ca/en/public-health/services/publications/diseases-conditions/report-heart-disease-Canada-2018.html


# Table of Contents
1. [Abstract](#abstract)
2. [Requirements](#requirements)
3. [Link to the Dataset](#link-to-the-dataset)
4. [Repository Content](#repository-content)
5. [Data Preparation](#data-preparation)
6. [Methodology](#methodology) 
7. [Results](#results)
8. [Study Conclusions](#study-conclusions)

# Abstract 
### Context of Problem	
Myocardial infarction (MI) refers to the loss of blood flow to the coronary artery of the heart, resulting in damage to the heart muscle due to a lack of oxygen supply (Lu, Liu, RongRong, & Zheng, 2015). The prognosis of MI is poor, with about half of patients developing complications that can worsen the trajectory of the disease or even lead to death (Golovenkin S. E., et al., 2020). Therefore, there is a strong need for clinicians to be able to predict complications of MI for more robust clinical decision making and better patient outcomes. The themes for this project are classification and predictive analytics.
### Project Theme and Research Questions
The themes for this project are classification and predictive analytics. The problem that this project will solve is how to predict complications of MI by addressing the following research questions: 
1) What medical history is most important for predicting MI complications? 
2) What symptoms at time of admission are most important for predicting MI complications? 
3) Do therapeutic interventions influence the patient’s final outcome? If so, which class of drugs and at which time points? 
### The Dataset
The ‘Myocardial infarction complications’ dataset consists of 1700 rows (patients) that are described by 111 clinical attributes and 12 possible MI complications. It was collected at the Krasnoyarsk Interdistrict Clinical Hospital in Russia from 1992 through 1995 but was only released publicly in 2020 (Golovenkin, et al., 2020). 
### Techniques and Tools
1)	Data Cleaning: The raw data will be cleaned to address issues such as missing values, outliers, imbalanced class distribution, and invalid values. Other transformations may need to be performed to improve data quality such as standardizing and normalizing values and renaming columns or values for consistency. 

2)	Exploratory Analysis: The distribution of attributes will be visualized by histograms for outlier detection and skewness. Correlation matrices using correlation coefficients such as Pearson and Cramér's V will be created to determine multicollinearity and feature selection. Statistical tests such as t-test and chi-square test will be performed for hypothesis testing. 

3)	Dimensionality Reduction: Feature selection by correlation analysis and feature importance using a learning vector quantization (LVQ) model will be performed.

4) Predictive Modeling: The dataset will be randomly split into training and test sets by a 7:3 ratio. Synthetic Minority Over-sampling Technique (SMOTE) will be performed on the training set to improve imbalanced class distribution. Classification algorithms such as random forest, naïve Bayes, logistic regression and neural networks will be applied for predictive modeling. Confusion matrices will be created to compare accuracy, precision, and recall of each supervised learning method. Other metrics will include the ROC curve and AUC. The run-time of each model will also be compared.  

The work will be performed in R Statistical Software version 4.0.3 (R Core Team, 2020) while descriptive statistics will be generated using Python version 3.8.5 (Van Rossum & Drake, 2009). The findings of this project will inform clinicians which supervised learning model is the most robust and which patient characteristics and clinical disease markers are most significant in predicting MI complications to improve disease management and prognosis.

# Requirements

R 4.0.3

Required packages are as follows: 

- dplyr
- tidyr
- rstatix
- ggpubr
- corrplot
- mlbench
- caret
- DMwR
- MASS
- e1071
- randomForest
- nnet
- pROC

Python 3.8.5

Required packages are as follows: 
- Pandas
- Pandas_Profiling
- SSL

# Link to the Dataset
https://leicester.figshare.com/articles/dataset/Myocardial_infarction_complications_Database/12045261/3

# Repository Content
The repository content is as follows: 
- The 'Constructed_Dataset' folder contains the dataset constructed from the data sources listed above. 
- The 'Checkpoints' folder contains the checkpoints of the study to date. Each model has one Python notebook checkpoint. 

# Data Preparation 
### Datasets
Datasets were obtained from the CMS website at the following addresses for the year 2020 (as available): 
- CMS Medicare Claims Quality Measures: https://data.cms.gov/provider-data/dataset/ijh5-nb2v
- CMS MDS Quality Measures: https://data.cms.gov/provider-data/dataset/djen-97ju
- CMS Provider Information: https://data.cms.gov/provider-data/dataset/4pq5-n9py
- CMS Survey Summary: https://data.cms.gov/provider-data/dataset/tbry-pc2d
- CMS COVID-19 Nursing Home Data: https://data.cms.gov/covid-19/covid-19-nursing-home-data

The following attributes were extracted from the above datasets as the independent variables within the dataset: 
- Federal Provider Number
- Provider Name
- Ownership Type 
- Number of Certified Beds
- Average Number of Residents per Day
- Long-Stay QM Rating
- Total nursing staff turnover
- Registered Nurse turnover 
- Adjusted Nurse Aide Staffing Hours per Resident per Day                                            
- Adjusted LPN Staffing Hours per Resident per Day                                                  
- Adjusted RN Staffing Hours per Resident per Day
- Number of Facility Reported Incidents
- Number of Substantiated Complaints
- Number of Citations from Infection Control Inspections
- Percentage of high risk long-stay residents with pressure ulcers
- Percentage of long-stay residents assessed and appropriately given the pneumococcal vaccine
- Percentage of long-stay residents assessed and appropriately given the seasonal influenza vaccine
- Percentage of long-stay residents experiencing one or more falls with major injury
- Percentage of long-stay residents who have depressive symptoms 
- Percentage of long-stay residents who lose too much weight
- Percentage of long-stay residents who received an antianxiety or hypnotic medication
- Percentage of long-stay residents who received an antipsychotic medication
- Percentage of long-stay residents who were physically restrained
- Percentage of long-stay residents whose ability to move independently worsened
- Percentage of long-stay residents whose need for help with daily activities has increased
- Percentage of long-stay residents with a catheter inserted and left in their bladder
- Percentage of long-stay residents with a urinary tract infection
- Percentage of low risk long-stay residents who lose control of their bowels or bladder
- Total Number of Health Deficiencies
- Total Number of Fire Safety Deficiencies
- Confirmed COVID-19 Cases Per Occupied Beds
- COVID-19 Deaths Per Occupied Beds

The dependent variable for this study was also extracted from the CMS Claims Data Set: 
- Adjusted Score (Number of outpatient emergency department visits per 1000 long-stay resident days)

The dataset from the 'Constructed_Dataset' folder may be used at this point for the next stages of the study. 

# Methodology 
The study methdology was as follows: 
| Step | Description |
| ------------- | ------------- |
| PROBLEM AND OBJECTIVE DEFINITION | Identify business context, define problem and related objectives. |
| DATA PREPARATION | Identify data sources and gather datasets in similar time periods.  Merge data sources and prepare data set for exploration. |
| DATA PREPROCESSING & EXPLORATION | Data cleaning (duplication elimination, missing value detection, error detection, outlier detection), transformation and normalization, descriptive statistics, univariate distribution analysis, bivariate correlation analysis (if required). |
| MODEL BUILDING & TESTING | Assumption testing for linear regression (Normality, linearity of IV-DV relationship, multicollinearity, homoscedasticity, autocorrelation, normal distribution of errors (Q-Q plots)), dimension reduction (as required), hyperparameter tuning, model fitting. |
| ANALYSIS | Split model into training and testing sets, conduct predictive analysis. |
| RESULTS & VALIDATION | Present results for all models include measures of model effectiveness, efficiency and stability. |
| INTERPRET & COMMUNICATE | Interpret results against evaluation metrics and present findings (report, presentation etc.). |

# Results
The following 3 models were built and evaluated: 
•	Stepwise Linear Regression
•	Gradient Boosted (XG Boost) Regression 
•	Kernel Ridge Regression 

<b>Summary performance measures for each model is as follows: </b>
| Model  | Stepwise Linear Regression | Gradient Boosted (XG Boost) Regression | Kernel Ridge Regression |
| ------------- | ------------- | ------------- | ------------- |
| Mean Absolute Error  | 0.05  | 0.05 | 0.05 |
| Root Mean Squared Error  | 0.004 | 0.005 | 0.005 | 
| R^2  | 0.138 | 0.262 | 0.305 |
| Training time  | 0.005s | 0.07s | 4.35s | 
| Prediction time | 0.001s | 0.003s | 0.23s |

The attributes with the most information gain in relation to the dependent variable are as follows: 
| Model  | Gradient Boosted (XG Boost) Regression | Kernel Ridge Regression |
| ------------- | ------------- | ------------- | 
| 1  | Long-Stay QM Rating (33.0)  | Total nursing staff turnover (0.908) | 
| 2  | Average Number of Residents per Day (31.0) | Percentage of long-stay residents whose need for help with daily activities has increased (0.100) | 
| 3 | Percentage of long-stay residents whose ability to move independently worsened (28.0) | Long-Stay QM Rating (0.084) | 
| 4  | Percentage of long-stay residents whose need for help with daily activities has increased (27.0) | Percentage of long-stay residents who were physically restrained (0.045) | 


# Study Conclusions
This study explored the relationship between nursing home quality measures and the long-stay patient outpatient ED Visit rate. The research questions focused on determining which quality measures significantly affect the ED Visit rate as well as which quality measures are able to predict the ED Visit rate for long-stay patients. Three models were built using Stepwise Regression, Gradient Boosted (XG Boost) Regression and Kernel Ridge Regression. The models were able to identify relationships between nursing home measures and outpatient ED Visit rate however a significant relationship was not established. The selected nursing home quality measures had 13% - 30% ability to predict the ED Visit rate, demonstrating that nursing home quality measures are not able to fully describe the ED Visit rate by itself. The Gradient Boosted (XG Boost) Regression and Kernel Ridge Regression models outperformed the Stepwise Regression model by a significant margin and were able to provide better predictive performance.

This study contributes to the body of knowledge regarding the impact of quality measures in the clinical, operational and safety domains on the outpatient ED Visit rate for long-stay patients within the nursing home environment. It identified that, while individual quality measures may contribute in part to the overall outpatient ED Visit rate for long-stay patients, there are many factors outside the realm of quality that predict ED Visit rate. However, this study was able to isolate a few quality-focused attributes such as ‘Long-Stay QM Rating’ and ‘Total Nursing Staff turnover’ that may have some impact on predicting the outpatient ED Visit rate within nursing homes that could be used in more comprehensive studies within this space. Additionally, a potential relationship between mobility and ED Visit rate was postulated, however additional research may be required. Clinical and operational quality measures were found to have a greater impact on predictive performance than safety measures. 

Further studies within this area can focus on exploring the relationship between clinical measures focused on mobility, ADLs and falls. Studies can additionally explore the relationship between aggregate quality measures and their predictive performance in relation to the nursing home long-stay outpatient ED Visit rate.
