# Logs

## Iteration 1.0 - predicting blood glucose as a regression problem
The first step was to create a simple baseline model that would not require any parameter tuning or complex methods. 
I first filled in the many mising values as follows:
- zero-

Note: the initial submission (best score with XGBoost) doesn't use the activity features.

## Iteration 1.1
- added the activity features and had the regressor accept categorical variables

## Iteration 2.0 - predicting blood glucose as time-series
- use a recurrent neural net
