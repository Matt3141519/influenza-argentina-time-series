# Influenza Argentina Time Series Forecasting

This project analyzes weekly influenza positivity in Argentina using data from WHO FluNet. The objective is to study the temporal structure of the series and compare forecasting models, including Holt-Winters and SARIMA.

The project was developed as a final assignment for a Time Series course.

## Objective

The main goal is to analyze and forecast weekly influenza positivity in Argentina.

Instead of modeling the absolute number of positive cases, the project focuses on the **positivity rate**, defined as the proportion of positive influenza samples among all processed samples. This provides a more robust measure when testing volumes vary over time.

## Dataset

The data comes from **WHO FluNet**, an international influenza surveillance platform maintained by the World Health Organization (WHO).

The original dataset contains weekly virological surveillance records for multiple countries and territories. For this project, the data was filtered to keep only records corresponding to Argentina.

The dataset file is not included in this repository because its size exceeds GitHub's browser upload limit.

To reproduce the notebook, download the file `VIW_FNT.csv` from WHO FluNet and place it inside the `data/` folder.

## Methodology

The project includes:

- Data cleaning and preprocessing
- Filtering records corresponding to Argentina
- Construction of a weekly time series
- Definition and analysis of influenza positivity
- Exploratory time series analysis
- Visualization of annual patterns
- Seasonal decomposition using STL
- Stationarity analysis using ADF and KPSS tests
- Train/test split
- Holt-Winters forecasting models
- SARIMA model selection and comparison
- Residual diagnostics
- Forecast evaluation
- Monthly resampling analysis
- Moving-average smoothing experiments

## Models Evaluated

The following forecasting approaches were considered:

- Holt-Winters Exponential Smoothing
- Weekly SARIMA models
- Monthly SARIMA models
- Moving-average-smoothed SARIMA models

Model selection was based on statistical criteria and forecast performance over a holdout test period.

## Evaluation Metrics

Forecast performance was evaluated using:

- MAE (Mean Absolute Error)
- MSE (Mean Squared Error)
- RMSE (Root Mean Squared Error)

Residual diagnostics were also considered through:

- ACF and PACF analysis
- Ljung-Box tests
- Residual visualization

## Main Findings

The influenza positivity series exhibits a clear annual seasonal pattern, with peaks typically occurring during the Argentine winter.

However, the timing and magnitude of those peaks vary substantially across years. In addition, the COVID-19 pandemic period introduced structural changes and atypical behavior that affected model performance.

Holt-Winters models provided a useful baseline but showed limitations when forecasting abrupt increases in influenza activity.

SARIMA models generally achieved better predictive performance, although residual diagnostics and forecast errors indicate that these models should be interpreted as forecasting baselines rather than definitive predictive solutions.

## Conclusions

The analysis confirms that influenza dynamics in Argentina contain strong seasonal components that can be partially captured using classical time series techniques.

While SARIMA models outperformed Holt-Winters in most comparisons, forecasting remains challenging due to changes in epidemiological behavior, testing intensity, and external shocks such as the COVID-19 pandemic.

Future work could incorporate exogenous variables such as climate indicators, mobility patterns, vaccination campaigns, or epidemiological covariates through SARIMAX or other multivariate forecasting approaches.

## Repository Structure

```text
influenza-argentina-time-series/
│
├── README.md
├── influenza_argentina_time_series_forecasting.ipynb
├── .gitignore
└── data/
    └── README.md
```

## Reproducibility

Some SARIMA model-selection cells may take several minutes to execute.

To reproduce the notebook, place the dataset file in the `data/` folder and use:

```python
d = "data/VIW_FNT.csv"
df = pd.read_csv(d, low_memory=False)
```

## Authors

- Matías Muñoz

Final project developed for a university course on Time Series Analysis.
