# Monthly Temperature Forecasting in Algiers Using SARIMA

## Project Overview

This project was developed as an individual assignment for the **Data Mining & Analytics (CCS2313)** course at Albukhary International University.

The project focuses on forecasting monthly average temperatures in Algiers, Algeria, using historical weather data from 1995 to 2020.

Three time series forecasting approaches were implemented and compared:

- Naïve Forecasting
- Seasonal Naïve Forecasting
- Seasonal Autoregressive Integrated Moving Average (SARIMA)

The objective was to evaluate how effectively each approach captures seasonal temperature patterns and predicts future observations.

## Dataset

**Source:** [Daily Temperature of Major Cities — Kaggle](https://www.kaggle.com/datasets/sudalairajkumar/daily-temperature-of-major-cities)

The original dataset contains over 2 million daily temperature records from cities worldwide.

For this project, the dataset was filtered to include Algiers, Algeria.

| Attribute | Description |
|---|---|
| Location | Algiers, Algeria |
| Period | January 1995 – May 2020 |
| Original Algiers Records | 9,266 daily observations |
| Processed Dataset | 305 monthly observations |
| Target Variable | Average Temperature (°F) |

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- Jupyter Notebook

## Methodology

### 1. Data Preprocessing

The following steps were performed:

- Filtered the dataset for Algiers, Algeria.
- Created a datetime index from the year, month, and day columns.
- Removed unnecessary columns.
- Replaced invalid temperature values (`-99`) with missing values.
- Applied linear interpolation to handle missing temperatures.
- Resampled daily records into monthly average temperatures.

The resulting dataset contains 305 monthly observations.

### 2. Train-Test Split

A chronological split was used to preserve the temporal order of observations.

- **Training:** 281 monthly observations
- **Testing:** Final 24 monthly observations

### 3. Forecasting Models

**Naïve Forecasting**

Uses the last observed training value as the prediction for every future month.

**Seasonal Naïve Forecasting**

Uses the temperature observed in the corresponding month of the previous year.

**SARIMA**

A seasonal statistical forecasting model designed to capture trends, autoregressive relationships, and recurring seasonal patterns.

The following configuration was used:

`SARIMA(1,1,1)(1,1,1,12)`

A seasonal period of 12 represents the annual temperature cycle.

### 4. Model Evaluation

The models were evaluated using:

- **MAE (Mean Absolute Error):** Average magnitude of prediction errors.
- **RMSE (Root Mean Squared Error):** Error metric that places greater weight on larger mistakes.
- **MAPE (Mean Absolute Percentage Error):** Average relative prediction error expressed as a percentage.

## Results

The original assignment reported the following results:

| Model | MAE | RMSE | MAPE |
|---|---:|---:|---:|
| Naïve | 8.92 | 10.26 | 13.6% |
| Seasonal Naïve | 2.25 | 2.51 | 3.5% |
| **SARIMA** | **1.38** | **1.62** | **2.2%** |

SARIMA achieved the lowest reported forecasting errors.

The Naïve model performed poorly because it did not account for seasonal temperature changes.

Seasonal Naïve improved performance by incorporating annual patterns.

SARIMA captured both temporal dependencies and seasonal fluctuations, producing predictions that more closely followed the observed temperatures.

## Data Visualization

The notebook includes visualizations of:

- Historical monthly temperature trends.
- Training and testing observations.
- Naïve and Seasonal Naïve predictions.
- SARIMA forecasts compared with actual temperatures.
- SARIMA prediction confidence intervals.

## Limitations

This repository preserves the original academic implementation.

The Seasonal Naïve model uses observed values from earlier months of the test period when predicting later months. SARIMA instead generates a 24-month forecast using the training data.

Therefore, the models do not use identical forecasting information for every prediction, and the reported scores should be interpreted with this limitation in mind.

The project also focuses on a single city and uses a predefined SARIMA configuration rather than an extensive hyperparameter search.

## How to Run

1. Clone or download this repository.
2. Install the required Python libraries:

```bash
pip install pandas numpy matplotlib statsmodels notebook
```

3. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/sudalairajkumar/daily-temperature-of-major-cities).
4. Place the dataset in the project directory and ensure its filename is `city_temperature.csv`.
5. Open `data mining assignment .ipynb` using Jupyter Notebook.
6. Run the cells sequentially to reproduce the analysis and forecasts.

## Repository Structure

```text
Algiers-Temperature-Forecasting/
├── data mining assignment .ipynb
└── README.md
```

The source dataset must be downloaded separately.

## Conclusion

This academic project explored the application of time series analysis to historical temperature data.

The reported results demonstrated that accounting for seasonality improved forecasting accuracy, with SARIMA achieving the lowest errors among the evaluated approaches.

The project provided practical experience in:

- Data Cleaning and Preprocessing
- Exploratory Data Analysis
- Time Series Forecasting
- Statistical Modeling
- Model Evaluation
- Data Visualization

## Author

**Khadiga Abdelkarim**

Computer Science (Data Science)

Albukhary International University

**Course:** CCS2313 — Data Mining & Analytics

**Project Type:** Individual Academic Assignment# Monthly-Temperature-Forecasting-in-Algiers-Using-SARIMA
