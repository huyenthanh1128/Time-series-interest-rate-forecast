# Time-series-interest-rate-forecast
# Vietnam 10Y Government Bond Yield Forecast (ARIMA-GARCH)

## Overview
This project implements a **time series forecasting model for Vietnam’s 10-year government bond yield** using a hybrid **ARIMA–GARCH framework**.

The approach combines:

- **ARIMA (AutoRegressive Integrated Moving Average)** to model the **conditional mean of bond yields**
- **GARCH (Generalized Autoregressive Conditional Heteroskedasticity)** to model **time-varying volatility in residuals**

This hybrid framework is widely used in financial markets because interest rate time series typically exhibit:

- Serial correlation
- Volatility clustering
- Non-stationary behavior

The model generates:

- Point forecasts of bond yields
- Volatility forecasts
- Prediction intervals
- Evaluation metrics on out-of-sample data

---
# Data
The model uses historical **Vietnam 10-year government bond yield data**.

### Dataset format

| Column | Description |
|------|------|
| Close | Daily 10Y government bond yield (%) |

If a datetime index is not present, the notebook automatically assigns a **business-day frequency starting from 2016-03-09**.

---

# Methodology

## 1. Data Preparation
- Load bond yield dataset
- Convert index to `DatetimeIndex`
- Plot historical yield movements

---

## 2. Train/Test Split

The dataset is split into:

- **Training set:** 80%
- **Test set:** 20%

This allows the model to be evaluated on **out-of-sample forecasts**.

---

## 3. Stationarity Check

Stationarity is tested using the **Augmented Dickey-Fuller (ADF) test**.

If the series is non-stationary:

- First differencing is applied
- Differenced series is used for model diagnostics

ACF and PACF plots help identify candidate ARIMA orders.

---

## 4. ARIMA Model Selection

A grid search is performed across:
p = 0-2
q = 0-2
d = 1

Models are evaluated using **Akaike Information Criterion (AIC)**.

The best model is selected as: ARIMA(p,d,q) with minimum AIC

This model captures the **conditional mean dynamics** of bond yields.

---

## 5. GARCH Volatility Model

Residuals from the ARIMA model are modeled with: GARCH(1,1)

This step captures **volatility clustering**, a common property in financial time series.

The conditional volatility series is estimated and plotted.

---

## 6. Rolling Forecast

The model performs **step-ahead forecasting**:

For each observation in the test set:

1. Forecast yield using ARIMA
2. Estimate volatility using GARCH on residuals
3. Update residual history
4. Generate prediction intervals

Outputs include:

- Forecasted yields
- Conditional volatility
- Confidence intervals

---

## 7. Model Evaluation

Forecast accuracy is evaluated using:

- **RMSE (Root Mean Squared Error)**
- **MAE (Mean Absolute Error)**

These metrics compare predicted yields with actual yields in the test set.

---

## 8. Future Forecast

After validation, the model is refit using **the full dataset**.

The notebook produces a **20-step forward forecast**, representing roughly:

- **1–4 weeks ahead (business days)**

Outputs include:

- Future yield forecasts
- Forecasted volatility

---

# Installation

Install required Python packages:

```bash
pip install pandas numpy matplotlib statsmodels scikit-learn arch



