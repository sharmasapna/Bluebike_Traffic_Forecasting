## BlueBike_Traffic_Forecasting

<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/bluebikepic.jpeg">

## Time Series Forecasting
### Some facts and terms related to time sereis forecasting 

Any time series(TS) can be split into:
- **Base Level**
- **Trend (increasing /decreasing slope)**
- **Seasonality (distinct pattern repeated over a regular time interval)**
- **Error**

Based on the trend the TS can be additive or multilplicative
- **Additive values**       = Base Level + Trend + Seasonality + Error
- **Multiplicative values** = Base Level * Trend * Seasonality * Error
We can use statsmodel.tsa.seasonal to decompsose the four elements of a time sereis.
- **Stationary** Data / Series is said to be stationary when mean, variance, autocorrelation are constant over time.<br>
  - Need for Stationarity: Auto regressive models are basically Linear regression models and we do not need the predictors to be correlated.
  - Approaches to make TS Stationary:
    - Differencing
    - Log transformation of Series
    - Taking tht nth log of the Series
    - Combination of the above
  - Test for Stationarity : 
    - ADH Test
    - KPPS Test
    - PP Test<br>
   If the p value calculated from these tests < 0.05, the Series is Stationary (Rejecting the Null Hypothesis: TS is **NOT** stationary    
- **Auto correlation** Correlation of series with previous values
- **Time series forecasting models**
  - Classical / Statistical Models — Auto Regression, Moving Averages, Exponential smoothing, ARIMA, SARIMA, TBATS(Linear Regression)
  - Machine Learning — XGBoost, Random Forest, or any ML model with reduction methods
  - Deep Learning — RNN, LSTM

## Basic Steps followed in Time Series Fore Casting: 
  1. Data extraction and Data cleaning
  2. [EDA](bluebikes_eda.ipynb)<br>
    2.1 Yearly bike ride pattern<br>
    2.2 Monthly bike ride pattern<br>
    2.3 Week-day bike ride pattern<br>
    2.4 Subscribers vs Customers distribution<br>
    2.5 Number of bikes per station<br>
    2.6 Time for which a bike is rented<br>
    2.7 Growth in the number of Subscribers<br>
    
    
### Some EDA Results are as follows:

<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/date-wise.png" width="900" height="300">
<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/EDA_Results.png">

<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/bb_subscriber_Customer_distrubution.png" width="300" height="300"><img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/bb_from_to stations_heatmap.png" width="300" height="300">

### Interactive plot of number of bikes 

<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/bokeh_plot.png" width="400" height="400"><br>

  3. Modeling<br>
    3.1 [Auto Regression Model](Bluebike_Demand_Forecasting_auto_regression.ipynb) 
      - 3.1.1 lag_plot
      - 3.1.2 auto- correlation plot
      - 3.1.3 acf plot
      - 3.1.4 prediction plot
  5. Results<br>
  6. Conclusions<br>
