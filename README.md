# Logs

## Iteration 1.0 - model blood glucose as a regression problem
The first step was to create a simple baseline model that would not require any parameter tuning or complex methods. 
I first filled in the many mising values as follows:
- zero-filled: insulin. I.e. assume no insulin was administered besides the one already present in the data
- mean-filled: blood-glucose (except bg-1+00), carbs and calories 
- forward, then backward filled: heart rate, steps. Here the assumption is that the heart rate or number of steps taken should be close to surrounding values and does not change much. 

Note: the initial submission (best score with XGBoost) doesn't use the activity features. The model gets a score of 2.6408.

## Iteration 1.1
- added the activity features and had the regressor accept categorical variables

## Iteration 2.0 - model blood glucose as time-series
- use a recurrent neural net with 1 LSTM layer
- intuitively, predicting blood glucose appears to be a seasonal time series type of problem (https://studiofarma.github.io/CGM-Innovation-Hub-Tech-Blog/Neural-Networks-for-time-series-forecasting/). I.e. the blood glucose throughout the day goes through seasons 

Preprocessing and feature engineering:
- make the time feature cyclical 
- dropped all activity features, participant number and id cols.

What I didn't do:
- denoise the data using rolling mean (i.e. smoothing the values based on a window with previous observations)

Notes on parameter tuning for the RNN:
- wider LSTM hidden size (> 64) seems to make the RNN untrainable (i.e. the loss does not decrease significantly). 
- batch size: batch size does not seem to change the learning much
- multiple LSTM layers: following the paper (https://inria.hal.science/hal-01571345/file/978-3-642-23957-1_29_Chapter.pdf) architecture of 20-12 neurons. Seems to decrease performance slightly. 
- dropout: added dropout of 0.2 for between LSTM and FC layer. Seems to decrease performance slightly.

The best RNN score is still worse than the default XGBoost score.


## TODO: 
- try out a GRU unit (usually trains better and is more stable)
- smooth out bg values.