## Predicting whether a loan will default or not

### Summary

This project builds on a Bank's data to develop a model that could predict which loans will default. The model succeeds on predicting which loans will be completly paid, but fails on predicting those that will not, mostly given the unbalance of the data.

## Introduction

Why are some credits unpaid? Does it occurre randomly, or can we predict when a client will default their obligations? Is there a pattern among a bank's clients that allowes us to know which loans will have to be overwritten? 

This research on the database of a Czech Bank will seek to develop a model that permit us to predict which loans will default. 

## Data

The data belongs to a Czech Bank and includes all the transactions of their clients database between the years 1994 and 1997. 

In order to build our mode, we focus on two types of loans, those with the status A and those with the status B:

* A stands for contracts finished without problems; whereas
* B stands for contracts finished without the loan being paid. 

To predict the outcome, we chose the following variables:

* Number of transactions;
* the age of the account;
* the unemployment rates from 1995 and 1996; 
* the amount of the loans;
* the number of crimes in the districts where the loans were contracted; 
* the date of birth of the account holder; and
* the ratio of payment of the loans. 

We control the dataset by only focusing in those loans where the account holder is the owner of the account. 

![variables](/Users/pedropablo/Documents/DAB/labs/lab_read_me/labreadme/Images "variables")

## Process

### 1. Preprocessing

We first make an exploratory analysis to see analyse the data. The first problem that arise is that very unbalanced data set, since the loans with status B make only 13,47% of the total.

The value counts are:

- A    203
- B     31

When analysing multicollinearity, we find some interesting outcomes, like that the unempoleyment is is negatively correlated with the number of crimes; meaning, the lower the unemployment, the lesser the amount of crimes. But the data does not allowes to extract conclusions, anecdotes beside.

![multicollinearity](/Users/pedropablo/Documents/DAB/labs/lab_read_me/labreadme/Images "multicollinearity")

To clean the data, we drop the columns that are not useful to our analizes, the Loan ID, and the type of client, owner or disponents, since we have excluded the lasts.

We transform the only categorical variable at this poin, which is the dependent variable, into a boolean 0-1 variable.

Finally, the rest of the variables, all numerical, we  normalize through a method from sklearn.

### 2. Processing

We then train our model of Logistic Regression using a scale of 30-70%. 

It gives us a ROC AUC (*Area under the receiver operating characteristic curve*) of 0.7817460317460317.

We visualise the result:
![ROC Visualization](/Users/pedropablo/Documents/DAB/labs/lab_read_me/labreadme/Images/ROC_visualization "ROC Visualization")

Finally, and in order to asses its accuracy, we visualize the results in a confussion matrix:

![Confussion Matrix](/Users/pedropablo/Documents/DAB/labs/lab_read_me/labreadme/Images "Confussion Matrix")

## Results

Unfortunately, our model fails to predict any of the defaulted loans. 
