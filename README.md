# TASK-2-MALL-# ⚡ Task 2 – Time Series Forecasting (Household Power Consumption)

This project performs **forecasting of household electricity consumption** using three different models: **ARIMA**, **Prophet**, and **XGBoost**. The goal is to predict future energy usage and compare model performances.

---

## 📁 Dataset

- **File:** `household_power_consumption.csv`
- **Source:** Household electric power consumption
- **Columns:** `Date`, `Time`, `Global_active_power`, etc.
- **Used Column:** `Global_active_power` (resampled hourly)

---

## 🎯 Objectives

- Parse and resample the time series data
- Engineer time-based features (hour, weekday, weekend)
- Train & compare:
  - ARIMA
  - Prophet
  - XGBoost
- Plot actual vs. predicted energy usage

---

## ⚙️ Steps Performed

### 1️⃣ Import Libraries

- `pandas`, `numpy`, `matplotlib`, `seaborn`
- `statsmodels`, `pmdarima`
- `prophet`
- `xgboost`, `sklearn`

### 2️⃣ Parse & Resample Data

- Combined `Date` and `Time` to create a proper `datetime` index
- Resampled to hourly average power usage using:

```python
df['Datetime'] = pd.to_datetime(df['Date'] + ' ' + df['Time'])
df.set_index('Datetime', inplace=True)
df_resampled = df['Global_active_power'].resample('H').mean().fillna(method='ffill')
