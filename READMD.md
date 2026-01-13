# Bike Demand Time-Series Forecasting

This repository contains my implementation and analysis of probabilistic time-series
models for short-term forecasting of hourly bike-sharing demand, using the
Capital Bikeshare dataset (2011–2012).

The project focuses on **forecasting accuracy and model behavior**, rather than
deep learning, and emphasizes careful target representation, stationarity analysis,
and evaluation methodology.

## Overview

Hourly bike rental demand exhibits strong daily and weekly seasonality, violating
the stationarity assumptions of classical time-series models. In this project, I:

- Remove deterministic seasonality using hour-based and hour × weekday averaging
- Analyze stationarity via ACF, PACF, and Augmented Dickey–Fuller tests
- Fit and compare probabilistic forecasting models on residual series
- Reconstruct forecasts to the original demand scale and analyze failure modes

## Models Implemented

- **ARMA models** (AR(2), ARMA(2,1))
- **Linear Dynamical Systems (LDS)** estimated via Kalman filtering

Models are evaluated using **rolling one-step-ahead forecasting** on a held-out
test set.

## Key Findings

- Removing **hour × weekday seasonality** produces the most stable residual series
  and consistently improves forecasting performance.
- **ARMA(2,1)** achieves the lowest MAE and RMSE across all target representations.
- LDS produces smoother forecasts but underperforms ARMA due to delayed response
  to sharp demand fluctuations.
- Residual-based forecasting can suffer reconstruction bias when seasonal patterns
  shift between training and test periods.

## Notes

Hidden Markov Models (HMMs) used for exploratory regime analysis are discussed in the
report but are **not implemented in this repository**, which focuses on forecasting
models.

