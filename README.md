# ROC Curve

I used 3 different datasets to build 3 different models to analyze the behavior of ROC curve, compare the result interpretations and introduce this method to my workmates.

Here I introduce one of the dataset and its model.

## Data source
Cardiovascular Disease dataset I ﬁnd on [Kaggle] (https://www.kaggle.com/sulianova/ cardiovascular-disease-dataset). 

This data set consists of 70 000 records of patients data, 11 features and a binary target variable to indicate whether the victim has an cardiovascular disease or not. This11 features could be clustered as 3 types: 
(1) Objective: factual information. Features of this type are quite streight forward. The age(by day), height(by cm), weight(by cm) and gender(categorical) of the victims all belong to this category. 
(2) Examination: results of medical examination. This includes the Systolic blood pressure(by mmHg), Diastolic blood pressure(by mmHg), Cholesterol(categorical) and Glucose(categorical). 
(3) Subjective: information given by the patient. This includes Smoking(binary), Alcohol intake(binary) and Physical activity(binary)

## Question Analyzed

Could the given features somehow indicate whether the victim has a cardiovascular disease or not? Analyze which feature could have positive or negative inﬂuence on catching the cardiovascular. And how could we evaluate the goodness of our model.

## Method

This dataset has both numeric and categorical explanatory variables and with a binary response. So, simple idea is to implement a Logistic regression to ﬁt the model. But there could be overﬁtting problems, like the relation between the Systolic blood pressure and Diastolic blood pressure. The lasso regression can control the overﬁtting.

So after the model ﬁtting of Logistic regression with Lasso, we usually use the ﬁtting accuracy of the test data to denote how well the model behaves. It’s intuitive if the accuracy itself is high enough. But when the accuracy is quite low, the AUC rate of ROC curve is more helpful to tell us what really happens.

## Result

From the model coeﬃcient, we can tell that older people are more likely to have cardiovascular disease. However, smoking, drinking alcohol and exercising could lower the chance. This is unusual. An reason for this is the dataset could be biased. The Subjective features oﬀered by victims may not be true. Also the record age is not the actual time they got the disease, but the time they knew they got the disease. But the results of medical examination do tell us how to get the pattern of this disease intuitively. Cholesterol must be the most important feature we should concern.

The accuracy is about 73% which is great. But a 79% AUC-ROC actually tell us how great the model is to distinguish between diﬀerent classes.

ROC curve is actually a really good way to access the model seperate capability among diﬀerent classed. Accuracy can tell us the model behavior with certain speciﬁty, but the ROC curve can tell us the model performance with diﬀerent speciﬁty, which is great. It’s a good accessment for classiﬁcation model. It only requires test data and predicted data, which is easy to implement.
