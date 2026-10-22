# Project Proposal
<div align='center', style="font-size: 24px"> Predictive Workforce Analytics: An XGBoost Model for Employee Attrition Identification </div>

## Overview
    This project applies the PACE Framework to develop, tune, and interpret an XGBoost classification pipeline that predicts employee attrition and identifies key organizational flight-risk drivers to enable proactive HR retention strategies.

>---

Milestone|Tasks|PACE Stages
---|---|---
M1| Defining the business problem, scope, and target metrics<br>Establsih data ethics safeguards|Plan
M2|Perform Exploratory Data Analysis on distributions, outliers, and class imbalance<br>Evaluate correlations with attrition<br>Perform data cleaning, categorical encoding, and formulate analytical hypothesis|Analyze
M3|Build Scikit-Learn Preprocessing Pipeline, Feature Engineering, and establish Train/Test data splits|Construct
M4|Build baseline model and XGBoost model and assess the metric scores<br>Optimize hyperparameters|Construct
M5|Synthesize findings into the final executive summary|Execute

## Foundations of Data Science
* Who is your audience for this project?
    - Salifort Motor's Human Resource (HR) department senior leadership team
* What are you trying to solve or accomplish? And, what do you anticipate the impact of this work will be on the larger business need?
    - The project's objective is to build a predictive model to determine whether an employee will leave based on different variables. This project will provide key insights on how to improve employee retention and managing the variables that increases the risk of employee churn.
* What questions need to be asked or answered?
    - What are the variables correlated to employee churn
    - Does department and salary directly correlated to employee churn
    - What employee performance metrics strongly predict employee churn
* What resources are required to complete this project?
    - Dataset
    - Data Dictionary
    - Packages and Libraries documentation
* What are the deliverables that will need to be created over the course of this project?
    - Project Proposal and Milestone Timeline
    - Exploratory Data Analysis (EDA) and visualization
    - Preprocessing Pipelines
    - Visual model results report
    - Hyperparameter Tuning
    - Executive Summary 
* How can you best prepare to understand and organize the provided information?
    - Feature classification
    - Feature Engineering
    - Model evaluation metrics documentation
* What follow-along and self-review codebooks will help you perform this work?
    - Course 1-5 Case Study notebooks
* What are a couple additional activities a resourceful learner would perform before starting to code?
    - Data entries inspection

## Go Beyond the Numbers: Translate Data into Insights
* What are the data columns and variables and which ones are most relevant to your deliverable?
* What units are your variables in?

    
        *  = relevant
Column|Dtype|Justification
---|---|---
satisfaction_level|[0-1] float64|omitted to focus on actionable workplace levers
last_evaluation*|[0-1] float64|for predicting if poor performance correlate to employee attrition
number_project|int64*|does workload affect employee attrition
average_montly_hours*|int64|does rendered hours also affect employee attrition
work_accident|int64|omitted; highly imbalanced
left*|int64|predictor variable
promotion_last_5years|int|omitted; highly imbalanced
department*|str (convert to binary)|does specific department contribute to employee attrition
salary*|str (convert to binary)|does salary level affects employee attrition

* What are your initial presumptions about the data that can inform your EDA, knowing you will need to confirm or deny with your future findings?
    - An average monthly hours for an employee is `160 hours per month` (8 hours, 5 days a week), with `50%` of employees worth more than 200 hours. This can suggest that employees are overworked.
$H_1$: Employee's `average_montly_hours` greater than 200 are more likely to left
    - employees with high `number_project` and work for more than `200` hours a month are more likely to left
    - `number_project` and `average_monthly_hours` are the main driver of employee attrition

* Is there any missing or incomplete data?
    - There are no incomplete or missing data in the dataset but contains duplicated entries
* Are all pieces of this dataset in the same format?
    - No. The dataset variables are mix of discrete and continuous numerical values and string and binary categorical variables
* Which EDA practices will be required to begin this project?
    - Discovering, Data Cleaning, Validation, Structuring, Visualization

## The Power of Statistics
* What is the main purpose of this project?
    - The main purpose of this project is to build a model that will help the Salifot Motors' HR department answer their question:

        _Salifort Motors Question:_ What’s likely to make the employee leave the company?
* What is your research question for this project?
    - How strong does XGBoost predicts outcomes
* What is the importance of random sampling? In this case, what is an example of sampling bias that might occur if you didn’t use random sampling?
    - Random sampling reduces the bias when using the complete data form the dataset. Sampling bias can overly represent an outcome when a class of a variables represents less than 20% of the total observed data points

## Regression Analysis: Simplify Complex Data Relationships
* Who are your stakeholders for this project?
    - Salifort Motors's HR Department Senior Leadership Team
* What are you trying to solve or accomplish?
    - Determining what's likely to make the employee leave the company
* What are your initial observations when you explore the data?
    - `average_montly_hours` have a very large values, which suggest that half of the employees are overworked
* What resources do you find yourself using as you complete this stage? (Make sure to include the links.)
    - Previous Case Studies
* Do you have any ethical considerations in this stage?
    - Training data bias

## The Nuts and Bolts of Machine Learning
* What am I trying to solve?
    - Determining what's likely to make the employee leave the company
* What resources do you find yourself using as you complete this stage?
    - Previous Case Studies
* Is my data reliable?
    - Yes. The scatterplots shows a pattern or clusters of data points which suggests that there are patterns that explains employee churn
* Do you have any additional ethical considerations in this stage?
    - None
* What data do I need/would I like to see in a perfect world to answer this question?
    - None
* What data do I have/can I get?
    - None
* What metric should I use to evaluate success of my business objective? Why?
    - F1 score which is the harmonic mean of precision and recall. F1 score changes depending on the difference between precision and accuracy, which is useful for imbalance dataset where accuracy fails to provide a good model score. 