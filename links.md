# Resources

## Courses and notebooks

- [Kaggle Learn, Time Series](https://www.kaggle.com/learn/time-series) is a
  free five-hour course covering trend, seasonality, lag features, Fourier
  features, and hybrid models.
- [Intro to Time Series Forecasting](https://www.kaggle.com/code/iamleonie/intro-to-time-series-forecasting)
  by iamleonie is a Kaggle notebook walking through chronological ordering,
  resampling, linear interpolation for gaps, and how to read a stationarity
  check.
- [Time Series Forecasting with Python](https://machinelearningmastery.com/time-series-forecasting-python/)
  at Machine Learning Mastery reframes a forecasting problem as a supervised
  learning dataset, one step at a time.

## Datasets

Each of the three is a CSV with a date column, so the work starts on features
rather than on a file format problem.

- [Store Item Demand Forecasting Challenge](https://www.kaggle.com/competitions/demand-forecasting-kernels-only)
  has five years of daily store-item sales across ten stores and fifty items.
  The Kaggle slug is `demand-forecasting-kernels-only` and does not match the
  title, which is worth knowing before searching.
- [Rossmann Store Sales](https://www.kaggle.com/competitions/rossmann-store-sales)
  adds promotions, holiday flags, competition distance, and store type, so the
  feature engineering has more to work with.
- [Walmart Store Sales Forecasting](https://www.kaggle.com/search?q=walmart+store+sales+forecasting)
  covers sales by department with weather, holiday flags, and fuel prices. The
  dataset page itself is no longer served, so this search URL is a stand-in.

## Theory and statistical methods

- [Forecasting: Principles and Practice](https://otexts.com/fpp3/), third
  edition, is a free textbook on stationarity, ETS, ARIMA, and the MAE, RMSE,
  and MAPE metrics. It is the broadest single source in this list.
- [Statsmodels time series analysis](https://www.statsmodels.org/stable/tsa.html)
  is the reference for ARIMA, SARIMAX, exponential smoothing, and the ADF
  stationarity test.

## Library documentation

Only the pages this project uses are listed.

- pandas. `.resample()` converts daily rows to weekly or monthly buckets,
  `.shift()` produces lag features, `.rolling()` computes moving averages, and
  the `.dt` accessors pull out month, day of week, and day of year.
- scikit-learn. `TimeSeriesSplit` handles time-aware cross-validation, and the
  [time series split section](https://scikit-learn.org/stable/modules/cross_validation.html#time-series-split)
  explains why a random shuffle leaks information across the split.
  `mean_absolute_error`, `mean_squared_error`, and `RandomForestRegressor` cover
  scoring and the tree baseline.
- XGBoost. The `XGBRegressor` class reference at
  [xgboost.readthedocs.io](https://xgboost.readthedocs.io/).
- Plotly Express. [plotly.com/python](https://plotly.com/python) covers hover,
  zoom, and per-point inspection of forecast values.
- Streamlit. `st.date_input`, `st.metric`, `st.line_chart`, and
  `st.plotly_chart` are the four widgets the dashboard needs. The
  [get started guide](https://docs.streamlit.io/get-started) covers a first app,
  and the [gallery](https://streamlit.io/gallery) has dashboard layouts for
  sales and inventory.

## Videos

Video titles and URLs change without notice, so each entry links to a search
rather than to a specific video ID.

- Rob Mulla on XGBoost for time series.
  [Search](https://www.youtube.com/results?search_query=Rob+Mulla+Time+Series+Forecasting+XGBoost).
  Covers turning date columns into lag and calendar features, and time-based
  splits that do not leak.
- StatQuest with Josh Starmer.
  [Trees](https://www.youtube.com/results?search_query=StatQuest+XGBoost) and
  [cross validation](https://www.youtube.com/results?search_query=StatQuest+Cross+Validation).
  Animated explanations of how decision trees split and how cross-validation
  runs internally.
- Data Professor (Chanin Nantasenamat) on a Streamlit app.
  [Search](https://www.youtube.com/results?search_query=Data+Professor+Streamlit+Machine+Learning).
  Wrapping a saved `.pkl` model in a web interface in under fifty lines.

## Optional frameworks and tooling

- [Prophet](https://facebook.github.io/prophet/) is Meta's library for daily
  business data with strong seasonal and holiday effects. A model fits in three
  lines, and the trend and seasonality components are plotted automatically.
- [LightGBM](https://lightgbm.readthedocs.io/) is a drop-in alternative to
  XGBoost that trains faster and holds less memory on wide tables.
- [StatsForecast](https://nixtlaverse.nixtla.io/statsforecast) and
  [NeuralForecast](https://nixtlaverse.nixtla.io/neuralforecast) from Nixtla
  cover classical and deep learning forecasters in compiled code. The
  `nixtla.github.io` address that used to be in this list is dead.
- [MLflow](https://mlflow.org/docs/latest/index.html) tracks metrics,
  hyperparameters, and model artifacts across runs.
- [Cookiecutter Data Science](https://cookiecutter-data-science.drivendata.org/)
  is the directory layout the repository already uses, so it is a reference
  rather than a starting point.
