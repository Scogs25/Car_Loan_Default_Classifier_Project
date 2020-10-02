# Car Loan Default Classifier Project
By Michael Scognamiglio
## Table of Contents
1. Project Overview
1. Business Case 
1. Repo Structure and Project Approach
1. Exploratory Data Analysis and Insights
1. Modeling 
1. Final Modeling and Analysis
1. Conclusions 
1. Next Steps
## Project Overview 
Car loans are one of the most common debts in America and Worldwide. In fact, there is over a trillion dollars in car loan debt in America alone. 
However, builiding a model that can identiy troublesome loans at a high rate is still very rare. Thus, this project strives to use EDA, statistical testing, and modal anaylsis to generate insights into what factors should be most strongly considered when looking at a borrower's ability to repay their car loans. Of Course, in the process I am also striving to create a useful model that lenders could use to flag 'bad loans'. This dataset was obtained from many Indian financial Institutions and compiled into one large dataset. The original dataset can be found on kaggle at the following link: https://www.kaggle.com/gauravdesurkar/lt-vehicle-loan-default-prediction.
## Business Case 
The inspiration for this project was the 2007-2008 finacial crisis that was largely due to the fact of 'bad home loans'. Of course, this project is about car loans but the idea is essentially the same. The ideal model for this project will be one that maximizes F1 Score. But more specifically, Recall is the metric that was considered the most during model selection. The idea being that by using Recall, we can minimize our false negatives and thus avoid labeling loans as 'safe' when they are anything but. Hopefully, a model like the one chosen could be used to avoid mass default and financial termoil in our modern globalized world. 
## Repo Structure and Project Approach
 All visulaizations used for both this Readme and the presenation pdf can be found in the pngs folder.
 The pdf 'How to Prevent a Car Loan Default Crisis" contains the  pdf presentation of this project.
 
 All of the code used during this project can be found in the jupyter notebooks folder. 
 The notebooks are in the following order:
 - Preliminary_Data_Cleaning_EDA.ipynb
    - This notebook contains all the code for the Data Cleaning and preliminary data exploration. 
    - One major goal of this notebook was to explore the data and through statistical testing and visulazations generate insights.
    - The other major goal of this notebook was to save a final dataframe to a csv after feature engineering/selection to use for Modeling
- Further_EDA_Preliminary_Modeling.ipynb
  - This notebook contains all the code for modeling comparisons and modeling selection as well as some futher statistical testing and feature engineering
  - The major goal was to create multiple different unique models and after using GridSearch to optimize hyper parameters, select the model that performed the best
- Final_Modeling_and_Analysis.ipynb
  -  This notebook's goal was to analyze the final selected model and see what insights could be found from it
  - This notebook also contains code for all the visualizations from Pre and Post modeling used for the presentation. 
##  Exploratory Data Analysis and Insights
This dataset consisted of over 200,000 rows and 60 distinct features. So, after spending quite some time exploring the entire dataset, One interesting feature was the identification used by a borrower when they applied for a car loan.  
![Image](https://raw.githubusercontent.com/Scogs25/Car_Loan_Default_Classifier_Project/master/pngs/How_ID_affects_Car_loan_defaults.png)
As you can see above, there is a drastic difference between people who used a Driver's License and defaulted compared to those who used an Aaadhar ID. 
An Aadhaar card is an identication card used by the Indian government which uses biometric data. There is not an exact equivalent in America for this card but the general idea remains the same.After looking a little closer, The Aadhar is given to practically everyone in India (reguardless of status or income). 
Thus, when looking at a borrower's personal info, pay close attention to what type of identication they posses. Those that have more 'official' documentation such as a Driver's license or Passport should be the safer bet. 
Two other features that recieved notable results were the CNS score (India's equivalent to credit score) and whether or not a borrower was salaried or not. 
![Image](https://raw.githubusercontent.com/Scogs25/Car_Loan_Default_Classifier_Project/master/pngs/How_Salary_and_Credit_Scroing_relates_to_Car_loan_Defaults.png)

Please keep in mind as there are two classes in this model with a value of zero representing a borrower that did not default. Thus, the y axis here is the average value for the target variable for each group. The point being the as the y axis value gets closer to one, then more people must have defaulted. 
Thus, the conclusion here would be prioritize applicants who have a salaried postion with a company over those who work for themselves but especiially if they do not have a very good credit score. In other words, a borrower with a high credit score and salaried should be a good bet to repay. 
However, A borrower that is not salaried and does not have a very good score is a serious risk. 
## Modeling 
- The first model was a logistic regression model. It performed surprisingly well reaching an F1 score of 65.4% and a Recall score of 90% on the test sets. 
- The second model was a KNN model that did not perfrom nearly as well achieved a F1 score of .55 and and A Recall Score of .56. 
- The third model was a Decison Tree and it actually performed the best out of all six different models. It achieved a F1 score of nearly .66  and a fantastic recall score of .927 on both the training and testing sets.  
- The fourth model was a Random Forest, which is essentially a lot of Decision Trees. It achieved a F1 score of .55 on the test set and a Recall score of .66. 
- The fifth model was an XGBoost model and it performed very similarly to the Random forest wtih an F1 score of .55 and Test Recall Score of .65. 
- The Last model used was an ensemble voting classifier. This model was essentially made up of the other five  models and then used the most common classification for each observation to make it's predicted classifictions. It achieved an F1 score of .654 and a recall score of .79 on the test set. It did have the highest overall acurracy at 58% while the other models were around 52% accuracy.  
Please note that one major issue with this dataset was large class imbalance. To resolve this, I downsampled the majority class before modeling. Also, all the values stated above were after each model's hyperparameters had been optimized with Gridsearch.
## Final Modeling and Anaylsis 
 After comparing models and weighing the advantages and consequences of each model, I decided to select the Decision Tree Model. 
 The primary reasons why I chose this model were due to it's performance and it's interpretability. The model achived a higher F1 score and Recall score than any other model. This was very important during selection because the model with the highest Recall Score would then have the least number of false positive observations. Interpretabilty also was an advantage because a decision tree allows you to visually see how and why observatons were split feature by feature. 
 Also, a decision tree allows you to see feature importances so you can see how each important each feature is relative to other features. 
 Thus, a Decison Tree allows you to see which features matter the most. Please see below to see what I mean.
 
 ![Image](https://raw.githubusercontent.com/Scogs25/Car_Loan_Default_Classifier_Project/master/pngs/Final_Model_Important_Features.png)
 
 ![Image](https://raw.githubusercontent.com/Scogs25/Car_Loan_Default_Classifier_Project/master/pngs/Decision_Tree_Visual.png)
 ## Conclusions 
  There were two  surpring and interesting conclusions I found from the modeling process. 
  Those would be the following:
  1. When looking at a large car loan, pay extra attention to that person's credit score becuase it will be very telling of whether or not they will default 
  1. Look closely at a borrower's accounts and any deliquency in terms of payment, espically for young people (early to mid 20s) and adults in their mid 40s or older. 
  Please see the following visualizations to see what I mean. 
  
  ![Image](https://raw.githubusercontent.com/Scogs25/Car_Loan_Default_Classifier_Project/master/pngs/How_High_Risk_and_Large_Principal_affect_Car_loan_Defaults.png)
  
  ![Image](https://github.com/Scogs25/Car_Loan_Default_Classifier_Project/blob/master/pngs/How_Age_and_Delinquent_Accounts_Influence_Loan_Defaults.png)
  
  The first insight makes common sense but the second insight surprised me. I would infer that these groups have particular trouble paying back loans if they have shown deliquency, because they have other financial restraints and responisibilities. In terms of the borrowers, in their 20s I would imagine college loans and low entry level salaries are to blame for inability to repay and as for Adults in their mid 40s and above, they may have many children at this age to care for which can be very expensive  or perhaps they  have a lot of debt from credit cards or a mortgage.
  ## Next Steps
  One weakness of this model was the fact that it was great at maximizing Recall and minimizing Type II error but in doing so it really reduced its's precision and 
  Type I Error increased. Thus, this led to way more false positives than would be ideal. I still chose the model though becase I prioritized false negatives so highly due to my business case. However, in the future, I would like to explore this further to see if I can try to find a better balance between these two parameters.
