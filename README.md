# Retail Sales Forecasting - Favorita Dataset

## Project Overview
This project focuses on time series forecasting of daily retail sales using historical data from Favorita grocery stores in Ecuador. The objective is to compare different forecasting approaches—statistical, business-oriented, and machine learning models—and determine which model provides the most reliable sales predictions for real-world retail planning.

Accurate sales forecasting is critical for inventory management, staffing decisions, and promotional planning. Retail sales data is inherently challenging due to seasonality, holidays, promotions, and external economic factors, making it an ideal use case for time series modeling.

By focusing on the Guayas region and the Top 3 product families (Grocery I, Beverages, and Cleaning), the project evaluates the trade-offs between machine learning, additive decomposition, and classical statistical models. The study covers a one-year testing window from August 16, 2016, to August 15, 2017.

## Problem Context

Retail planners require dependable demand forecasts to:
- Reduce stockouts and overstocking
- Optimize supply chain and logistics
- Improve operational efficiency
- Support data-driven business decisions

This problem is challenging due to:
- Strong weekly and yearly seasonality
- Holiday effects and irregular events
- Non-stationary time series behavior
- Large-scale historical datasets

## Data Overview

The project uses the Favorita Grocery Sales Forecasting dataset, covering daily sales data from January 2013 to August 2017.

Key datasets include:
- `train.csv` – Daily item-level sales data
- `holidays_events.csv` – National and local holidays
- `oil.csv` – Daily oil prices (economic indicator)
- `stores.csv` – Store metadata
- `items.csv` – Product metadata
- `transactions.csv` – Daily transaction counts per store

## Target variable:
- unit_sales (aggregated to daily total sales for modeling)

## Limitations:
- High aggregation required for classical models
- External regressors not fully exploited in all models
- Computational constraints for large-scale modeling

## Methodology

Three different forecasting approaches were implemented and evaluated:

**1. ARIMA / SARIMAX (Statistical Model)**
- Aggregated daily total sales
- Stationarity checks (ADF test) and first-order differencing applied
- ARIMA(1,1,1) baseline extended to SARIMAX with weekly seasonality (s=7), holiday flag, and oil price as external regressors
- Suitable for capturing trend, seasonality, and external factor effects in a univariate setting

Notebook:
**[ARIMA / SARIMAX Model](Notebooks/02_Favorita_ARIMA_Forecasting.ipynb)**

**2. Prophet (Business-Oriented Model)**
- Daily aggregated sales
- Automatic handling of trend and seasonality
- Built-in holiday effects
- Minimal feature engineering required

Notebook:
**[Prophet Model](Notebooks/03_Favorita_PROPHET_Forecasting.ipynb)**

**3. XGBoost (Machine Learning Model)**
- Supervised learning formulation of the time series
- Feature engineering including:
  - Lag features (1, 7, 14, 28 days)
  - Rolling averages and standard deviations
  - Calendar-based features (day of week, month, weekend flag)
  - External regressors (holiday flag, oil price)
- Baseline model followed by early stopping optimization
- Most flexible but computationally intensive approach

Notebook:
**[XGBoost Model](Notebooks/04_Favorita_XGBoost_Forecasting.ipynb)**

**Data Preparation:**
**[Data Preparation Notebook](Notebooks/01_Favorita_Data_Prep.ipynb)**

## Evaluation Metrics

All models were evaluated using the same metrics to ensure fair comparison:
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- Bias (systematic over/underprediction)

Additionally:
- Actual vs. predicted values were visualized
- Residual diagnostics were performed for each model

## Model Comparison Summary
Models were evaluated based on their ability to minimize error during high-volatility retail events.

| Model Strategy | Mean Absolute Error (MAE) | Root Mean Squared Error (RMSE) |
| :--- | :--- | :--- |
| **Prophet Baseline** | **~285.8** | **~485.1** |
| Prophet + Holidays | ~285.3 | ~484.5 |
| XGBoost Optimized | ~288.6 | ~499.3 |
| XGBoost Baseline | ~291.3 | ~500.9 |
| SARIMAX | ~316.8 | ~497.7 |
| ARIMA | ~343.4 | ~548.4 |

* Under a clean and conservative evaluation framework, Prophet outperformed XGBoost and ARIMA, demonstrating that simpler, well-specified time-series models can surpass more complex machine learning approaches when tuning and feature engineering are constrained.
* It is noted that reported XGBoost performance in the literature often relies on extensive hyperparameter optimization or less strict evaluation protocols. Therefore, the results presented here emphasize methodological robustness over maximal predictive performance.
* All models significantly outperform a naive baseline (MAE: 429.57), confirming that each approach adds real predictive value.


## Prepared by :
**Author:** Sevil Kücük

**Date:** January 2026

Masterschool Data Science Course
