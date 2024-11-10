# Logs

## Iteration 1.0 - model blood glucose as a regression problem
The first step was to create a simple baseline model that would not require any parameter tuning or complex methods. 
I first filled in the many mising values as follows:
- zero-

Note: the initial submission (best score with XGBoost) doesn't use the activity features.

## Iteration 1.1
- added the activity features and had the regressor accept categorical variables

## Iteration 2.0 - model blood glucose as time-series
- use a recurrent neural net
- intuitively, predicting blood glucose appears to be a seasonal time series type of problem (https://studiofarma.github.io/CGM-Innovation-Hub-Tech-Blog/Neural-Networks-for-time-series-forecasting/). I.e. the blood glucose throughout the day goes through seasons 

## TODOs:
1. Look into time series preprocessing (https://towardsdatascience.com/preprocessing-time-series-data-for-supervised-learning-2e27493f44ae) 