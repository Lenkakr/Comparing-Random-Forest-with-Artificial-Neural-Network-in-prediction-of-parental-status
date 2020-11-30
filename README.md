# Comparing Random Forest with Artificial Neural Network in prediction of parental status in 50+ adults

## Introduction to the project

Project compares the success of Random Forest machine learning method and deep learning method Artificial Neural Networks in predicting whether a 50+ respondent is parent or not. This project aims to answer a research question, whether there is a significant difference in socio-demographic characteristics and social support networks of adults older than 50 years old  based on their parental status (whether they have children or not). It aims to answer whether we can predict that person was parent or childless based on a set of socio-demographic characteristics and characteristics of social support networks.

**Dataset** comes from the SHARE project (Survey of health, ageing and retirement in Europe) available [here](http://www.share-project.org/home0.html). The data collection runs since 2004 every 2-3 years and nowadays is conducted in 27 European countries and Israel. In total there has been 7 waves of SHARE released. This project uses the 6th wave (2015), as 7th wave had a substantial amount of missing data in modules focusing on social support networks. 6th wave also had a special module about social networks of respondents. 

The data is organized into thematic modules, which can be easily merged and analysed together. Modules of interest in this projects are social networks module, social support module, and imputations module, which contains important socio-demographic variables of respondents.


## Problem formulation

**Data points** are each individual Czech respondent older than 50 years old.

**Features** are socio-demographic characteristics and characteristics of social networks of each individual respondent. Dataset for example includes age, marital status, size of social network, whether respondent received any social support in last 12 months, and many (in total 49) more.

**Labels** of the data are in a variable parent, which describes whether respondent is a parent (1) or nonparent (0). This variable is created based on variable number of children. These labels were picked on the basis of past analysis of the topic, when social support received in old age was analysed using logistic regression. In this analysis, the parental status was used as a feature and was proven to be not significant in prediction of receipt of social support. Therefore, the question of what are the features creating significant differences between parents and nonparents was risen up. This project will attempt to answer this question.

Dataset is split into test and validation data for model evaluation. The model could be also evaluated on the base of data from other countries in Europe (provided their profile is similar to Czech republic), or based on wave 4 that also collected data on social networks and was conducted in 2011.


## Methods

As two methods to compare I chose Random Forest and Artificial Neural Network (ANN). I wanted to compare success of machine learning algorithm with deep learning algorithm in this numerical binary classification task. These two algorithm were picked purposely, as they tend to overfit the data, which is a occurance that very rarely happens in social research.


## Hypothesis space

In this project I am using non-linear hypothesis space of Random Forest and ANN. The choice was make conciously, as these algorithms do not require robust feature preprocessing. In follow-up analysis, comparison to linear hypothesis space, for example of logistic regression, could be useful.


## Loss function

For Random Forest the loss function was the Area Under the Receiver Operating Characteristic Curve (ROC AUC), which was computed from prediction scores. Our target value is binary so it’s a binary classification problem. AUC is a good way for evaluation for this type of problems. The accuracy was observed as well, together with confusion matrix that gives a useful insight of false positives and false negatives. Extra focus was also put on recall for the nonparent class, as the target variable is unbalanced with minority class being nonparents.

In ANN the binary crossentropy was chosen as loss function, together with binary accuracy of predictions. Confusion matrix was used to observe how competent model is in classes prediction, with emphasis on recall for nonparent class.
