# Applications of Supervised Machine Learning Methods for the Prediction of Myocardial Infarction Complications in Hospital Patients

## Abstract
Context of Problem	

Myocardial infarction (MI) or heart attack refers to the decrease or loss of blood flow to the coronary artery of the heart, resulting in damage to the heart muscle due to a lack of oxygen supply (Lu, Liu, RongRong, & Zheng, 2015). The prognosis of MI is poor, with about half of patients developing complications that can worsen the trajectory of the disease or even lead to death (Golovenkin, et al., 2020). Therefore, there is a strong need for clinicians to be able to predict complications of MI for more robust clinical decision making and better patient outcomes.

Project Theme and Research Questions

The themes for this project are 1) classification and 2) predictive analytics. The problem that this project will solve is how to predict complications of MI using various patient information. To address this problem, the following research questions will be addressed:
1.	What medical history is most important for predicting MI complications?
2.	What symptoms and vital signs at time of admission are most important for predicting MI complications?
3.	Do therapeutic interventions influence the patient’s final outcome? If so, which class of drugs and at which time points?


The Dataset

The ‘Myocardial infarction complications’ dataset consists of 1700 rows (patients) that are described by 111 clinical attributes and 12 class variables containing possible MI complications. It was collected at the Krasnoyarsk Interdistrict Clinical Hospital in Russia from 1992 through 1995 but was only released publicly in 2020 (Golovenkin, et al., 2020). A small portion (7.6%) of the dataset contains missing values. 
  
Techniques and Tools

1.	Data Preparation: The raw data will be cleaned to address inconsistencies such as missing values, outliers, imbalanced class distribution, duplicate records or columns, and invalid values. Other transformations may need to be performed to improve data quality such as standardizing and normalizing values, one-hot encoding of categorical variables, discretizing numeric attributes to categorical, and renaming columns or values for consistency. 

2.	Exploratory Analysis: The distribution of attributes will be visualized by histograms for outlier detection and skewness. Correlation matrices using correlation coefficients such as Pearson and Cramér's V will be calculated to determine multicollinearity and optimize feature engineering. Statistical tests such as t-test and chi-square test will be performed for hypothesis testing and dimensionality reduction.

3.	Predictive Modeling: The dataset will be randomly split into training and test sets by a 7:3 ratio. Synthetic Minority Over-sampling Technique (SMOTE) will be performed on the training set to improve imbalanced class attributes. Classification algorithms such as random forest, naïve Bayes, logistic regression, and neural networks will be applied for predictive modeling. Confusion matrices will be created to compare accuracy, precision, and recall of each supervised learning method. Other metrics will include the ROC curve and AUC. 

	The data cleaning and exploratory analysis will be performed in R Statistical Software version 4.0.3 (R Core Team, 2020) while the modeling will be performed in Python version 3.8.5 (Van Rossum & Drake, 2009). R packages such as dplyr, tidyr, stringr, corrplot, and ggplot and Python packages such as Pandas, Numpy, Scikit-learn, and Matplotlib will be used. 
  
	The findings of this project will inform clinicians which supervised learning model is the most robust and which patient characteristics and clinical disease markers are most significant in predicting MI complications to improve disease management and prognosis.
