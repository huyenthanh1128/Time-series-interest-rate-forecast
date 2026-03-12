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

# Project Structure
