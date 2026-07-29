U.S. Imports of Goods from World - Forecasting in R

This project analyzes monthly U.S. imports of goods on a customs basis using the FRED series IMP0015 and compares multiple time series forecasting approaches in R.
The workflow includes exploratory analysis, variance stabilization, stationarity testing, ARIMA and ETS modeling, benchmark comparison, and out-of-sample forecast evaluation.


Project goal

The goal is to identify an accurate and interpretable model for forecasting monthly U.S. imports of goods from the world using data from 2000 to 2026.
The analysis evaluates whether more complex models such as seasonal ARIMA and ETS outperform simpler benchmark methods like naive and seasonal naive forecasts.


Dataset

* Source: FRED, series IMP0015.
* Dataset link: https://fred.stlouisfed.org/series/IMP0015.
* Variable: U.S. imports of goods, customs basis, measured in millions of U.S. dollars.
* Frequency: Monthly.
* Analysis window: 2000-01 to 2026-05.
* Not seasonally adjusted.



Methods

The project uses a modern R forecasting workflow built with tsibble, feasts, and fable.
The series is log-transformed to stabilize variance, then assessed for stationarity using KPSS, ndiffs(), and nsdiffs() before candidate models are specified.

Methods included:

* Time plot and log-scale visualization.
* First, seasonal, and double differencing diagnostics.
* ACF/PACF analysis of the differenced series to assess autocorrelation structure and support model interpretation and ARIMA specification.
* Automatic ARIMA and ETS estimation.
* Benchmark comparison with naive and seasonal naive models.
* Residual diagnostics using residual ACF and Ljung-Box tests.
* Out-of-sample forecast evaluation using RMSE, MAE, and MAPE.
* Back-transformation of forecasts to the original scale for interpretability.


Key findings

The analysis finds that one non-seasonal difference is sufficient after log transformation, while seasonal differencing is not required, so the series is modeled with d=1 and D=0 in the ARIMA framework.
Although the automatic ARIMA model provides the strongest in-sample fit among the formal time series models, residual diagnostics still show some remaining autocorrelation, 
and ETS performs worse by both information criteria and residual behavior.
On the held-out test set, the seasonal naive model achieves the lowest RMSE, MAE, and MAPE on both the log scale and the back-transformed original scale.
This suggests that strong and stable yearly seasonality is the dominant feature of the series and that a simple benchmark can outperform more complex models in practice.


Tools and packages

* R
* tidyverse
* lubridate
* tsibble
* feasts
* fable
* fabletools
* readr
* scales


Repository contents

* US_imports_of_Goods_from_World.Rmd — main analysis and forecasting workflow.
* IMP0015.csv — input dataset used in the project.


Main takeaway

This project highlights an important forecasting lesson: more sophisticated models do not always produce better predictions.
For this dataset, the seasonal naive model offers the best balance of accuracy and simplicity for short-term forecasting.


Skills demonstrated

- Time series forecasting in R.
- Log transformation, stationarity testing, and differencing.
- ARIMA, ETS, naive, and seasonal naive model comparison.
- Forecast evaluation using RMSE, MAE, and MAPE.
- Residual diagnostics with ACF and Ljung–Box tests.
- Communicating technical results in a reproducible R Markdown workflow.
  

Author: Monica Boghean, MBA in Business Analytics Data analytics, visualization, and forecasting portfolio project


