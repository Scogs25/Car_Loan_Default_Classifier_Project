# Car_Loan_Default_Classifier_Project
By Michael Scognamiglio
## Table of Contents
1. Project Overview
1. Business Case and Approach
1. Repo Structure and Project Approach
1. Exploratory Data Analysis and Insights
1. Modeling 
1. Final Modeling and Analysis
1. Conclusions and Next Steps
## Project Overview 
Car loans are one of the most common debts in America and Worldwide. In fact, there is over a trillion dollars in car loan debt in America alone. 
However, builiding a model that can identiy troublesome loans at a high rate is still very rare. Thus, this project strives to use EDA, statistical testing, and modal anaylsis to generate insights into what factors should be most strongly analyzed when looking at a borrower's ability to repay their car loans. Of Course, in the process I am also striving to create a useful model that lenders could use to avoid 'bad loans'. This dataset was obtained from many Indian financial Institutions and compiled into one large dataset. The original dataset can be found on kaggle at the following link: https://www.kaggle.com/gauravdesurkar/lt-vehicle-loan-default-prediction.
## Business Case 
The inspiration for this project was the 2007-2008 finacial crisis that was largely due to the fact of 'bad home loans'. Of course, this project is about car loans but the idea is essentially the same. The ideal model for this project will be one that maximizes F1 Score. But more specifically, Recall is the metric that was used during model selection. The idea being that by using Recall, we can minimize our false negatives and thus avoid labeling loans as 'safe' when they are anything but. Hopefully, a model like the one chosen could be used to avoid mass default and financial termoil in our modern globalized world. 
## Repo Structure and Project Approach
 All visulaizations used for both this Readme and the presenation pdf can be found in the pngs folder.
 All of the code used during this project can be found in the juoyter notebooks folder. 
 The notebooks are in the following order:
 - Preliminary_Data_Cleaning_EDA.ipynb
    - This notebook contains all the code for the Data Cleaning and preliminary data exploration. 
    - One major goal of this notebook was to explore the data and through statistical testing and visulazations generate insights.
    - The other major goal of this notebook was to save a final dataframe after feature engineering/selection to use for Modeling
- Further_EDA_Preliminary_Modeling.ipynb
  - This notebook contains all the code for modeling comparisons and modeling selection as well as some futher statistical testing and feature engineering
  - The major goal was to create multiple different unique models and after using GridSearch to optimize hyper parameters, select the model that performed the best
- Final_Modeling_and_Analysis.ipynb
  -  This notebook's goal was to analyze the final selected model and analyze it to see what insights could be found from the model
  - This notebook also contains code for all the visualizations from Pre and Post modeling 
##  Exploratory Data Analysis and Insights
This dataset consisted of 200,000 rows and 60 distinct features. So, after spending quite some time exploring the entire dataset, One interesting feature was the identification used by a borrower when they applied for a car loan.  
![Image](https://raw.githubusercontent.com/Scogs25/Car_Loan_Default_Classifier_Project/master/pngs/How_ID_affects_Car_loan_defaults.png)
As you can see above, there is a drastic difference between people who used a Driver's License and defaulted compared to that used an Aaadhar ID. Btw, Aadhaar is an identication card used by the Indian government which uses biometric data. There is not an exact equivalent in America for this card but the general idea remains the same.When looking at a borrower's personal info, pay close attention to what type of identication they posses. Those that have more 'official' documentation such as a Driver's license or Passport should be the safer bet. 
Two other features that recieved notable results were the CNS score (India's equivalent to credit score) and whether or not a borrower was salaried or not. 
![Image](https://raw.githubusercontent.com/Scogs25/Car_Loan_Default_Classifier_Project/master/pngs/How_Salary_and_Credit_Scroing_relates_to_Car_loan_Defaults.png)

Please keep in mind as there are two classes in this model with a value of zero representing a borrower that did not default. Thus, the y axis here is the average value for the target variable for each group. The point being the one closer to one means more and more borrowers who defaulted. 
Thus, the conclusion here would be prioritize applicants who have a salaried postion with a company over those who for themselves but espicially if they do not have a very good credit score. In other words, a borrower with a high credit score and salaried should be a good bet to repay. However, A borrower that is not salaried and does not have a very good score is a serious risk. 
## Modeling 
The first model was a logistic regression model. After optimizing hyperparameters with GridSearch, It performed surprisingly well reaching an F1 score of 65.4% and a Recall score of 90% on the test sets. The second model was a KNN model that did not perfrom nearly as well achieved a F1 score of .55 and and A Recall Score of .56. The third model was a Decison Tree and it actually performed the best out of all six different models. It achieved a F1 score of nearly .66  and a fantastic recall score of .927 on both the training and testing sets.  The fourth model was a Random Forest, which is essentially a lot of Decision Trees. It achieved a F1 score of .55 on the test set and a Recall score of .66. The fifth model was an XGBoost model and it performed very similarly to the Random forest wtih an F1 score of .55 and Test Recall Score of .65. The Last model used was an ensemble voting classifier. This model was essentially made up of the other five  models and then used the most common classification for each observation to make it's predicted classifictions. It achieved an F1 score of .654 and a recall score of .79 on the test set. It did have the highest overall acurracy at 58% while the other models were around 52% accuracy.  
One other note class imbalance was a major issue with this dataset so prior to modeling I chose to use downsampling to. 
The first model was a logistic regression model. After optimizing hyperparameters with GridSearch, It performed surprisingly well reaching an F1 score of 65.4% and a Recall score of 90% on the test sets. The second model was a KNN model that did not perfrom nearly as well achieved a F1 score of .55 and and A Recall Score of .56. The third model was a Decison Tree and it actually performed the best out of all six different models. It achieved a F1 score of nearly .66  and a fantastic recall score of .927 on both the training and testing sets.  The fourth model was a Random Forest, which is essentially a lot of Decision Trees. It achieved a F1 score of .55 on the test set and a Recall score of .66. The fifth model was an XGBoost model and it performed very similarly to the Random forest wtih an F1 score of .55 and Test Recall Score of .65. The Last model used was an ensemble voting classifier. This model was essentially made up of the other five  models and then used the most common classification for each observation to make it's predicted classifictions. It achieved an F1 score of .654 and a recall score of .79 on the test set. It did have the highest overall acurracy at 58% while the other models were around 52% accuracy.
Please note that one major issue with this dataset was large class imbalance. To resolve this, I downsampled the majority class before modeling. 
## Final Modeling and Anaylsis 



