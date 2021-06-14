# Supervised Application and Transaction Fraud Models

This repository contains code decks and reports on two supervised fraud detection algorithms.  These projects were completed in collabration with 6 other teammates, for their privacy I have redacted their names.  Any juypter notebook with (teammate) in the title was not completed by myself, and the (joint) file was completed in collabaration with two others.  All code is heavily based off the frameworks that were provided in our class.

Here's an Executive Sumamry of Each Project

# Application Fraud (Project 2)

This project focuses on using advanced analytical modeling and techniques to find identity fraud.
Identity fraud is the act of misrepresenting who you are in order to improperly receive services or
to remain “hidden” while conducting illegal activity. There are three core methods of identity
fraud: identity theft, identity manipulation, and using synthetic identity. Our goal was to use only
identity fields to build a model for flagging potential application/identity fraud in real time.
Our dataset was synthetic generated from analysis of over one billion real US applications over a
ten year period. The data was created to attempt to mimic real application data and contained
over one million records with various personally identifiable information fields including social
security number, first and last name, address, date of birth, and home phone number.
 
We started by cleaning the data set of any frivolous fields, common values used to fill missing
fields, and replaced them with unique values. We created over 350 candidate variables by linking
applications through different combinations of identity fields. These candidate variables included
a risk table for the day of the week, days since last seen for a specific attribute, velocity which
captures the number of times an attribute appears in the past n days, and relative velocity, a ratio
between recent occurrences and longer time periods for an attribute.

In order to prepare our dataset for model building, we used a filter and wrapper feature selection
process to reduce the total number of variables. First, we ran a filter, which selected the variables
with the highest average KS and FDR rank. Next, we used RFECV, a backward selection
wrapper, to rank and narrow our field of variables. Lastly, we ran RFE, without cross validation,
to get a well-ranked list of 30 different candidate variables.

Using our 30 most-important variables, we created 43 unique models from four different binary
classification algorithms: Logistic Regression, Random Forest, XGBoost, and Neural Networks.
Each of these models used an unique combination of sampling strategies and hyperparameters.
Based on the best performance on the test set, we selected XGBoost, a gradient boosting
algorithm, as our final model with 600 estimators, a max depth of 3 for each estimator, a learning
rate of 0.1, and a subsample ratio of 0.8. This model produced a fraud detection rate for 3% of
the population at 53.56%. The success of our final model demonstrates a real business
opportunity to implement our solution as an effective way of catching identity fraud.

# Transaction Fraud (Project 3) 

This project focuses on using advanced analytical modeling and techniques to find transaction
fraud. Transaction fraud is a type of financial fraud that occurs during the usage process through
unauthorized transactions. Example modes of transaction fraud include lost/stolen cards,
counterfeit cards, or other account take-overs. Approximately 47% of US consumers have
indicated that they have experienced transaction fraud, resulting in a $40 billion global loss each
year. Our goal was to use transaction information to build a model for flagging potential
transactional fraud in real-time.

Our dataset was collected from a US government organization and contained actual credit card
purchases from January to December of 2010. The flagged frauds were synthetically generated
from an industry expert with previous experience in card transaction behavior. The data
contained over 96,000 records with transaction detail fields including the card number, merchant
number, merchant state, merchant zip code, a description of the merchant, and the amount.
We started by cleaning the data set by mapping the missing merchant numbers, states, and zip
codes and removed all transactions that weren’t of purchase type. We created over 1,900
candidate variables by linking transaction information through different combinations of our
original fields. These candidate variables included a day of the week risk table, days since last
seen for a specific attribute, frequency which captures the number of times an attribute appears in
the past n days, and velocity change, a ratio between recent occurrences and longer time periods.
Additionally, we used natural language processing to assign transactions to an industry category
and geographical information to track the distance between a purchase zip code and a customer's
point of origin.

In order to prepare our dataset for model building, we used a filter and wrapper feature selection
process to reduce the total number of variables. First, we ran a filter, which selected the top 200
variables with the highest average KS and FDR rank. Next, we used forward stepwise selection
to get a well-ranked list of 15 different candidate variables.

Using our 15 most-important variables, we created 33 unique models from four different binary
classification algorithms: Logistic Regression, Random Forest, XGBoost, and Neural Networks.
Each of these models used an unique combination of sampling strategies and hyperparameters.
Based on the best performance on the test set, we selected Random Forest, an ensemble
algorithm, as our final model with 50 estimators, a max depth of 10 for each estimator, 300 min
samples split, and a SMOTE oversampling technique. This model produced a fraud detection
rate for 3% of the population at 63.13%. With our recommended cutoff of 5.9%, our model will
provide an annualized financial savings of $1.4 million. The success of our final model
demonstrates a real business opportunity to implement our solution as an effective way of
stopping transaction fraud saving money for our customers and the business.
