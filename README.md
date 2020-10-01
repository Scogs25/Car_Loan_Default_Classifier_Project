# Car_Loan_Default_Classifier_Project
By Michael Scognamiglio
## Table of Contents
1. Project Overview
1. Business Case and Approach
1. Repo Structure and Project Approach
1. Exploratory Data Analysis and Inferences 
1. Modeling 
1. Final Modeling and Analysis 
## Project Overview 
Car loans are one of the most common debts in America and Worldwide. In fact, there is over a trillion dollars in car loan debt in America alone. 
However, builiding a model that can identiy troublesome loans at a high rate is still very rare. Thus, this project strives to use EDA, statistical testing, and modal anaylsis to generate insights into what factors should be most strongly analyzed when looking at a borrower's ability to repay their car loans. Of Course, in the process I am also striving to create a useful model that lenders could use to avoid 'bad loans'. This dataset was obtained from many Indian financial Institutions and compiled into one large dataset. The original dataset can be found on kaggle at the following link: https://www.kaggle.com/gauravdesurkar/lt-vehicle-loan-default-prediction.
## Business Case 
The inspiration for this project was the 2007-2008 finacial crisis that was largely due to the fact of 'bad home loans'. Of course, this project is about car loans but the idea is essentially the same. The ideal model for this project will be one that maximizes F1 Score. But more specifically, Recall is the metric that was used during model selection. The idea being that by using Recall, we can minimize our false negatives and thus avoid labeling loans as 'safe' when they are anything but. Hopefully, a model like the one chosen could be used to avoid mass default and financial termoil in our modern globalized world. 
## Repo Structure and Project Approach
 All visulaizations used for both this readme and the presenation pdf can be found in the pngs folder.
 All of the code used during this project can be found in the juoyter notebooks folder. 
 It is the following order:
 - Preliminary_Data_Cleaning_EDA.ipynb
    - This notebook contains all the code for the Data Cleaning and preliminary data expolration. 
    - One major goal of this notebook was to explore the data and through statistical testing and visulazations generate insights.
    - The other major goal of this notebook was to save a final dataframe after feature engineering/selection to use for Modeling
- Further_EDA_Preliminary_Modeling.ipynb
  - This notebook contains all the code for modeling comparisons and modeling selection as well as some futher statistical testing and feature engineering
  - The major goal was to create multiple different unique models and after using GridSearch to optimize hyper parameters, select the model that performed the best
- Final_Modeling_and_Analysis.ipynb
  -  This notebook's goal was to analyze the final selected model and analyze it to see what insights could be found from the model
  - This notebook also contains code for all the visualizations from Pre and Post modeling 
