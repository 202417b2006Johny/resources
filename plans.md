# Project plan

## Eight-week schedule

**Weeks 1 and 2, data and concepts.** The Kaggle Time Series course runs first.
The Store Item Demand dataset is then loaded into a notebook and charted by
month and by day of week to expose the seasonal shape of the data.

**Weeks 3 and 4, feature engineering.** Calendar features (`dayofweek`,
`month`, `year`), lag features (`sales_lag_7`, `sales_lag_30`), and rolling
statistics (`rolling_mean_7`) are generated in `ml_demandforecast/features.py`.

**Weeks 5 and 6, model and metrics.** The split is chronological, training on
years 1 to 4 and testing on year 5. A baseline of `RandomForestRegressor` or
`XGBRegressor` is trained against that split, then scored with MAE, RMSE, and
MAPE.

**Week 7, dashboard.** The trained model is written to `models/` with
`joblib.dump`. A Streamlit app loads it, accepts a date range and a store
selector, and plots the forecast with Plotly.

**Week 8, documentation.** Limitations are written down explicitly, for example
that the model assumes future promotion frequency matches the historical rate.
The demo is rehearsed.

## Team roles

Five roles, one per member. File paths match the Cookiecutter Data Science
layout already in the repository, which has no `src/` or `app/` directory.

| Role | Files | Report section owned |
| --- | --- | --- |
| Data and EDA | `notebooks/01_eda.ipynb`, `ml_demandforecast/dataset.py` | Exploratory Data Analysis and Business Context |
| Feature engineering | `ml_demandforecast/features.py` | Feature Selection and Data Transformation Methodology |
| Primary model | `ml_demandforecast/modeling/train.py` | Primary Model Architecture and Tuning |
| Baselines and comparison | `ml_demandforecast/modeling/train.py` | Model Benchmarking, Error Metrics and Performance Comparison |
| Dashboard and deployment | `app.py` at the repository root | System Architecture, User Guide and Practical Limitations |

The feature engineering role carries the most technical work, since lag and
rolling features are where most of the modelling gains come from and where a
mistake silently leaks future data into training.

The primary model and the baselines both live in `train.py`. Splitting them into
`train.py` and `baselines.py` would avoid two people editing one file.

## Minimum viable scope

Four items are enough to end up with a trained model and a working dashboard.
Everything in the optional section below is additional.

1. **Dataset.** Kaggle's Store Item Demand Forecasting. It is already clean, so
   no preparation time is lost.
2. **Video.** Rob Mulla's XGBoost time series tutorial, which covers feature
   engineering and time-aware splits in under 30 minutes.
3. **Model.** `xgboost.XGBRegressor` or `sklearn.ensemble.RandomForestRegressor`.
4. **Dashboard.** Streamlit, as a single `app.py` showing interactive line
   graphs.

## Optional additions

Both drop in behind the same interface, so neither requires a change to the
dashboard.

- **Prophet.** Built for daily business data with seasonal trends and holidays.
  A model fits in three lines, and the trend and seasonality components are
  plotted automatically.
- **LightGBM.** A drop-in replacement for XGBoost that trains faster and holds
  less memory on large tabular data.
