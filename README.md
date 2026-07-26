# London Air Quality Time-Series Forecasting

An end-to-end time-series forecasting project analyzing and predicting daily nitrogen dioxide (NO₂) concentrations in London.

The project uses historical measurements from the London Air Quality Network, focusing on the Kensington and Chelsea – North Ken monitoring site between 2010 and 2023.

## Project Objective

The objective was to:

- explore long-term and seasonal patterns in daily NO₂ concentrations;
- prepare a reliable daily time series;
- compare statistical, machine-learning and forecasting models;
- evaluate the final models on the unseen 2023 test period;
- identify the strengths and limitations of each forecasting approach.

## Dataset

- Location: Kensington and Chelsea – North Ken, London
- Pollutant: Nitrogen dioxide (NO₂)
- Original frequency: Hourly
- Forecasting frequency: Daily mean
- Training period: 2010–2022
- Test period: 2023

Days containing fewer than 18 hourly measurements were treated as missing. Missing daily observations were handled chronologically without using future test information.

Data source: [London Air Quality Network](https://www.londonair.org.uk/LondonAir/Default.aspx)

The data is provided by the Environmental Research Group at Imperial College London and is licensed under the Open Government Licence.

## Project Workflow

1. Data loading and quality assessment
2. Hourly-to-daily aggregation
3. Missing-value analysis and treatment
4. Exploratory time-series analysis
5. Trend and seasonal decomposition
6. Stationarity testing
7. ACF and PACF analysis
8. Baseline forecasting
9. ARIMA and SARIMA modelling
10. Prophet optimisation
11. Feature engineering for machine learning
12. Time-based cross-validation
13. HistGradientBoostingRegressor tuning
14. Final model comparison
15. Residual analysis

## Models Evaluated

- Mean baseline
- Naive baseline
- Seasonal Naive baseline
- Drift baseline
- ARIMA
- SARIMA
- Prophet variants
- HistGradientBoostingRegressor

## Final Results

| Model | MAE | RMSE | MAPE (%) |
|---|---:|---:|---:|
| Tuned HistGradientBoostingRegressor | 5.913 | 8.152 | 54.240 |
| Advanced Prophet | 6.968 | 10.395 | 52.742 |
| SARIMA(0,1,5)(0,1,1,7) | 8.889 | 11.381 | 89.285 |
| ARIMA(2,1,5) | 9.311 | 11.658 | 100.055 |
| Naive | 9.402 | 14.163 | 50.099 |
| Seasonal Naive | 10.018 | 14.130 | 84.468 |
| Drift | 10.190 | 14.880 | 52.886 |
| Mean | 16.484 | 18.114 | 196.145 |

The Tuned HistGradientBoostingRegressor achieved the lowest MAE and RMSE on the unseen 2023 test period.

The Naive baseline obtained the lowest MAPE. However, MAPE must be interpreted carefully because percentage errors become unstable when observed NO₂ concentrations are close to zero.

## Key Findings

- Daily NO₂ concentrations exhibit clear annual seasonality.
- Concentrations are generally higher during autumn and winter and lower during summer.
- The long-term trend decreased considerably between 2010 and 2022.
- Statistical models captured regular temporal patterns but produced overly smooth forecasts.
- The machine-learning model achieved the strongest MAE and RMSE results.
- Abrupt pollution peaks remained difficult to predict.
- Weather, traffic and exceptional-event data could improve future predictions.

## Validation Strategy

The data was split chronologically:

- 2010–2022: training and model development
- 2023: final unseen test period

Time-based expanding-window cross-validation was used for model selection and tuning. The 2023 test data remained excluded from this process.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Statsmodels
- Prophet
- Scikit-learn
- Jupyter Notebook / Google Colab

## Complete Notebook

[Open the complete London Air Quality forecasting notebook](./London_Air_Quality_Time_Series_Forecasting.ipynb)

## Limitations and Future Improvements

Potential improvements include:

- adding weather variables such as temperature, wind and precipitation;
- incorporating traffic-intensity data;
- including public holidays and exceptional pollution events;
- evaluating additional boosting and deep-learning models;
- creating prediction intervals suitable for non-negative concentrations;
- testing the approach across multiple London monitoring sites.

## Author

Tatiana Tchouakam Chouacheu

Data Scientist & AI Engineer | Business Analyst

- [YouTube – TatianaBuildsData](https://youtube.com/@tatianabuildsdata)
- [GitHub](https://github.com/TatianaTchouakam)

## Licence and Attribution

The historical air-quality data was obtained through the London Air Quality Network and is licensed under the Open Government Licence.

This repository contains the analytical code and project documentation created for educational and portfolio purposes.
