## Capacity Planning for Bluebike
### A project done by Dewanshi Deswal, Sapna Sharma and Sarang Pandey as a Capstone project for DS5500, Northeastern University,Boston.



<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/bluebikepic.jpeg">

## Abstract
[Bluebike](https://www.bluebikes.com/) is a bike sharing system with over 1800 bicycles and 308 fixed stations across Boston. The growth of the biking system over the last decade encapsulates the need of redefining business supply. The purpose of this project is to forecast hourly station level demand by implementing the Prophet, Random Forest and XGBoost models. The models are trained on a rolling basis and evaluated using matrices including the Root Mean Square Error(RMSE), R-Squared and Mean Absolute Error(MAE). These models are used to make decisions to improve inventory balancing resulting in increased profits and customer satisfaction.      
## Problem Description
Blue bike is a bike rental facility in Boston that allows individuals to use it for a short trip for a price. The customer can borrow a bike from a blue bike station scattered throughout the city and return it to another or the same station. Due to the topography of the city and localization of popular sites such as shopping complexes, offices, and educational facilities some stations have more demand for starting or ending a trip. This phenomenon leads to an imbalance in the bike inventory, which is currently maintained by a set of trucks operated to monitor the demand and supply. Inefficiency in the execution of the repositioning process using a manual approach leads to an increase in operating costs and customer dissatisfaction. There is a potential for reducing operational costs and improving customer satisfaction with improved decision-making based on predictive analysis. The primary purpose of the project is to determine the station demand and solve the demand-supply problem.  We aim to identify the number of bikes to be added or removed from a station at the best optimal time.
## Dataset and Preprocessing 
The Boston Bluebike [dataset](https://www.bluebikes.com/system-data) owned and maintained by the municipalities provides historical trip data for 350+ stations. Each of the 10 million trip records includes information for start and end date-time of the trip, duration of the trip, start and end station name, latitude and longitude of the station, and user membership type. Additional significant attributes including weekday/weekend, holiday, hour of the data was feature engineered to the dataset. The data were then pre-processed to remove 0.5% of the trips which included trips with a distance greater than 10 miles and trip duration exceeding 2 hours. The average trip duration was 19 mins. We also restricted the data to start from January 1st, 2019 till August 31st, 2021. Data is available in the data folder.

The Boston local hourly weather data provided by the National Center for Environmental Information (NOAA) includes the weather attributes consisting of the temperature, precipitation, and wind speed. The weather data was merged with the blue bike trip data to create a unified data source.


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
  1. Data extraction and Data cleaning<br>
    1.1 Monthly Zip files were downloaded and csv files were extracted<br>
    1.2 Data Cleaning<br>
    1.3 [Serializaion](Bluebikes_Serialize_Csv_Files.ipynb)<br>
  3. [EDA](bluebikes_eda.ipynb)<br>
    2.1 Yearly bike ride pattern<br>
    2.2 Monthly bike ride pattern<br>
    2.3 Week-day bike ride pattern<br>
    2.4 Subscribers vs Customers distribution<br>
    2.5 Number of bikes per station<br>
    2.6 Time for which a bike is rented<br>
    2.7 Growth in the number of Subscribers<br>
    
    
### Some EDA Results are as follows:

<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/date-wise.png" width="450" height="150">
<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/EDA_Results.png">

<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/Hourly_Weekday_Heatmap.png" width="400" height="200"><img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/bb_from_to stations_heatmap.png" width="200" height="200">

### Interactive plot of number of bikes 

<img src="https://github.com/sharmasapna/BlueBike_Traffic_Forecasting/blob/main/data/bokeh_plot.png" width="200" height="200"><br>

  3. Feature Engineering<br>
    3.1 Adding the holiday feature <br>
    3.2 Adding the weather data for temperature, humidity and windspeed<br>
    3.2 Outlier removal <br>
  4. Modeling<br>
  - 4.1 [Auto Regression Model](Bluebike_Demand_Forecasting_auto_regression.ipynb) <br>
      - 4.1.1 lag_plot<br>
      - 4.1.2 auto- correlation plot<br>
      - 4.1.3 acf plot<br>
      - 4.1.4 prediction plot<br>
  - 4.2 [Moving Average Model](Bluebike_Demand_Forecasting_Moving_Averages.ipynb)<br>
      - 4.2.1 Trailling Moving Average<br>
      - 4.2.2 Best window size Calculation<br>
  - 4.3 [Arima](Bluebike_Demand_Forecasting_Arima.ipynb)<br>
  - 4.4 Prophet<br>
  - 4.5 [LSTM](Bluebike_Demand_Forecasting_lstm_MIT_Mass_Av.ipynb)<br>
  - 4.6 Random Forest<br>
  - 4.7 [XGBoost](Bluebike_Demand_Forecasting_linear_regression_xgboost.ipynb)<br>
  5. Results<br>
  - 5.1 Hourly Forecasting for selected stations with high outbound traffic<br>
  - 5.2 Recommendation<br>
    - 5.2.1 Lower price for off peak hours
    - 5.2.2 Just in time bike refilling schedule to reduce the operation cost
  6. Future works
