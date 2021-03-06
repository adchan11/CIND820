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
3. [Link to the Dataset and Data Dictionary](#link-to-the-dataset-and-data-dictionary)
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
1)	Data Cleaning and Preparation: The raw data will be cleaned to address issues such as missing values, outliers, imbalanced class distribution, and invalid values. Other transformations may need to be performed to improve data quality such as standardizing and normalizing values and renaming columns or values for consistency. 

2)	Exploratory Analysis: The distribution of attributes will be visualized by histograms for outlier detection and skewness. Correlation matrices using correlation coefficients such as Pearson and Cramér's V will be created to determine multicollinearity and feature selection. Statistical tests such as t-test and chi-square test will be performed for hypothesis testing. 

3)	Dimensionality Reduction: Feature selection by correlation analysis and feature importance using a learning vector quantization (LVQ) model will be performed.

4) Predictive Modeling: The dataset will be randomly split into training and test sets by a 7:3 ratio. Synthetic Minority Over-sampling Technique (SMOTE) will be performed on the training set to improve imbalanced class distribution. Classification algorithms such as random forest, naïve Bayes, stepwise logistic regression and neural networks will be applied for predictive modeling. Confusion matrices will be created to compare accuracy, precision, recall, and F1 score of each supervised learning method. Other metrics will include the ROC curve and AUC. The training run-time of each model will also be compared.  

The work will be performed in R Statistical Software version 4.0.3 (R Core Team, 2020). The findings of this project will inform clinicians which supervised learning model is the most robust and which patient characteristics and clinical disease markers are most significant in predicting MI complications to improve disease management and prognosis.

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
- bestNormalize
- DataExplorer

# Link to the Dataset and Data Dictionary
https://leicester.figshare.com/articles/dataset/Myocardial_infarction_complications_Database/12045261/3

# Repository Content
The repository content is as follows: 
- The 'Code and Technical Reports' folder contains an R Markdown file with the rendered HTML technical report and other assignment files.
- The 'Figures' folder contains the images used in this README file. 

# Data Preparation 
The following attributes were extracted as the independent variables within the dataset based on the research questions: 
- AGE
- SEX
- INF_ANAM
- STENOK_AN
- FK_STENOK
- IBS_POST
- IBS_NASL
- DLIT_AG
- ZSN_A
- nr_11
- nr_01
- nr_02
- nr_03
- nr_04
- nr_07
- nr_08
- np_01
- np_04
- np_05
- np_07
- np_08
- np_09
- np_10
- endocr_01
- endocr_02
- endocr_03
- zab_leg_01
- zab_leg_02
- zab_leg_03
- zab_leg_04
- zab_leg_06
- GB
- SIM_GIPERT
- S_AD_KBRIG
- D_AD_KBRIG
- S_AD_ORIT
- D_AD_ORIT
- O_L_POST
- K_SH_POST
- MP_TP_POST
- SVT_POST
- GT_POST
- IM_PG_P
- GIPO_K
- K_BLOOD
- GIPER_NA
- NA_BLOOD
- ALT_BLOOD
- AST_BLOOD
- KFK_BLOOD
- L_BLOOD
- ROE
- n_p_ecg_p_12
- fibr_ter_01
- fibr_ter_02
- fibr_ter_03
- fibr_ter_05
- fibr_ter_06
- fibr_ter_07
- fibr_ter_08
- NA_KB
- NOT_NA_KB
- LID_KB
- NITR_S
- NA_R_1_n
- NA_R_2_n
- NA_R_3_n
- NOT_NA_1_n
- NOT_NA_2_n
- NOT_NA_3_n
- LID_S_n
- B_BLOK_S_n
- ANT_CA_S_n
- GEPAR_S_n
- ASP_S_n
- TIKL_S_n
- TRENT_S_n
- any_complication

There are 12 different class variables (i.e. complications) in the dataset but they are all severely imbalanced. Therefore, a new class variable titled ‘any_complication’ will be derived from all 12 class variables such that 0/FALSE means the patient had no complications at all and 1/TRUE means the patient had one or more complications. 

# Methodology 
The study methdology was as follows: 

<p align="center">
  <img src="Figures/Methodology.png">
</p>



| Step | Description |
| ------------- | ------------- |
| DATA CLEANING and  PREPARATION | Fix and remove incorrect, corrupted, incorrectly formatted, duplicate, missing or incomplete data. Perform data normalization and standardization. Perform data transformations as needed. |
| EXPLORATORY ANALYSIS | Descriptive statistics, univariate distribution analysis (histograms), statistical hypothesis testing, correlation analysis. |
| DIMENSIONALITY REDUCTION | Feature selection by correlation analysis and rank importance. |
| PREDICTIVE MODELING | Split model into training and testing sets. Perform SMOTE to fix imbalance class distribution. Apply supervised learning machine learning methods. |
| VALIDATION | Compare results for all models using metrics such as accuracy, precision, recall, F1 score, ROC, AUC and training run time. |
| DISCUSSION | Interpret results and discuss limitations and future work. |

# Results
The following 4 models were built and evaluated: 
- Random Forest
- Naïve Bayes
- Stepwise Logistic Regression
- Neural Networks

<b>Summary performance measures for each model is as follows: </b>
| Model  | Random Forest | Naïve Bayes | Stepwise Logistic Regression | Neural Networks |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| Accuracy  | 0.6925  | 0.6329 | 0.6885 | 0.6349 |
| Precision  | 0.7712 | 0.8268 | 0.7799 | 0.7634 |  
| Recall | 0.6921 | 0.4901 | 0.6689 | 0.5662 |
| F1 Score | 0.7295 | 0.6154 | 0.7201 | 0.6502 |
| AUC | 0.693 | 0.668 | 0.693 | 0.652 |
| Training Run Time  | 4.690 s | 0.009 s | 0.651 s | 0.395 s |

<b>Rank of Feature Importance<b>
 
 <p align="center">
  <img src="Figures/Feature Importance.png">
</p>
 
 ```
ROC curve variable importance

  only 20 most important variables shown (out of 72)

           Importance
AGE            0.6429
NA_R_1_n       0.5875
STENOK_AN      0.5782
FK_STENOK      0.5737
NITR_S         0.5677
SEX            0.5671
ZSN_A          0.5561
Systolic       0.5503
L_BLOOD        0.5466
LID_S_n        0.5465
ROE            0.5454
DLIT_AG        0.5440
NA_KB          0.5432
endocr_01      0.5425
zab_leg_02     0.5416
K_BLOOD        0.5413
NA_BLOOD       0.5400
ANT_CA_S_n     0.5400
INF_ANAM       0.5368
B_BLOK_S_n     0.5327
 ```

<b>Most Stastistically Significant Features by Correlation Analysis<b>
| Variable         |
| ---------------- |
| AGE              |
| SEX              |
| INF\_ANAM        |
| STENOK\_AN       |
| FK\_STENOK       |
| DLIT\_AG         |
| ZSN\_A           |
| nr\_03           |
| nr\_04           |
| endocr\_01       |
| zab\_leg\_02     |
| zab\_leg\_03     |
| GB               |
| O\_L\_POST       |
| K\_SH\_POST      |
| MP\_TP\_POST     |
| IM\_PG\_P        |
| GIPO\_K          |
| Systolic         |
| K\_BLOOD         |
| L\_BLOOD         |
| ROE              |
| n\_p\_ecg\_p\_12 |
| fibr\_ter\_02    |
| NA\_KB           |
| NITR\_S          |
| NA\_R\_1\_n      |
| NA\_R\_2\_n      |
| NA\_R\_3\_n      |
| B\_BLOK\_S\_n    |
| ANT\_CA\_S\_n    |
| ASP\_S\_n        |
| TIKL\_S\_n       |

# Study Conclusions
TBD
