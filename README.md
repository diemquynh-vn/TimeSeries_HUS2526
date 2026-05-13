# TimeSeries_HUS2526

## Global CO2 Emission Forecasting
### Overview 
Climate change and global warming represent the most significant challenges of the 21st century, primarily driven by the increase in greenhouse gases, specially CO2 from fossil fuels. This project aims to build robust time series and machine learning models to forecast emission trends, providing data-driven insights to support emission reduction policies and sustainable development goals.

### Dataset 
The analysis is based on historical global CO2 emission data spanning from 1750 to 2024. 
- Observations: 275 data points.
- Features: year, totalCO2 (measured in tonnes).
- Preprocessing: The data underwent logarithmic transformation to stabilise variance and reduce right-skewness. Differencing was applied to achieve stationarity, verified by the Augmented Dickey-Fuller (ADF) test.

### Methodology 
The project explores three main categories of forecasting models: 
- State Space Models (SMM): Implementation of a Local Linear Trend model using the Kalman Filter to estimate hidden states (level and slope) representing the long-term trend of CO2 trend.
- Classical Time Series Models:
  - Holt's Linear Trend: Extrapolates stable trends withour losing the momentum of increase/decrease.
  - ARIMA: The optional model was identified as ARIMA(1,1,0) with drift, selected via grid search to minimize AIC/ BIC.
- Machine Learning Models:
  - Linear Regression: Used as a baseline model with lag features (lag1, lag2).
  - Random Forest & XGBoost: Employed to capture non-linear relationships, with hyperparameters optimized through Time Series Cross Validation.
 
### Results 
Models were evaluated using RMSE, MAE, and MAPE:
- Top performance: Linear Regression yielded the lowest error rates (RMSE = 0.0320) for this specific dataset. 
- Statistical Model:
  - SSM was more accurate than both ARIMA and Holt in terms of RMSE and MAE. However, when it comes to capturing the actual trend for future values it appears to overestimate more significantly than the top-performing model.
  - ARIMA and Holt models performed consistently well, with MAPE values below 5%, effectively capturing the long-term upward trend.
- Machine Learning: While Random Forest and XGBoost captured the trend, they showed high errors and had more difficulty generalizing logn-term trends compared to simpler models.
