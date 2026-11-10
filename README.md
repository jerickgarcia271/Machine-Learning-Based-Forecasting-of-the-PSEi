
# Machine Learning-Based Forecasting of the Philippine Stock Exchange Index (PSEi)

## Overview

This project develops machine learning models to **forecast the Philippine Stock Exchange Index (PSEi) over the next five trading days** using historical market data and technical indicators. The study compares three regression algorithms—**Linear Regression, Random Forest, and XGBoost**—to determine their effectiveness in predicting the index's upcoming weekly price.

The project incorporates historical OHLC (Open, High, Low, and Close) prices, trading volume, and technical indicators representing market trend, volatility, and momentum. It also evaluates the models against a **Naive Walk (Random Walk) baseline**, a fundamental benchmark in financial time-series forecasting.

The project demonstrates the application of machine learning and statistical evaluation in financial forecasting, highlighting the importance of baseline comparisons when assessing the predictive capabilities of more complex models.

---

## Project Highlights

- Developed machine learning models to forecast the PSEi's price over the next five trading days.
- Utilized approximately **15 years of historical PSEi data**, spanning October 2011 to October 2026.
- Engineered technical indicators including the **50-day Simple Moving Average (SMA), 14-day Relative Strength Index (RSI), and 14-day Average True Range (ATR)**.
- Compared Linear Regression, Random Forest, and XGBoost against a Naive Walk baseline.
- Achieved an **R² of 0.8779** using Linear Regression.
- Found that Linear Regression marginally outperformed the Naive Walk in MSE, RMSE, and R², while the Naive Walk achieved a slightly lower MAE.

---

## Objectives

The project aims to:

- Forecast the PSEi's price approximately five trading days ahead using historical market data.
- Incorporate technical indicators to represent market trends, volatility, and momentum.
- Compare the predictive performance of Linear Regression, Random Forest, and XGBoost.
- Evaluate machine learning models against a Naive Walk baseline.
- Demonstrate the application of feature engineering, time-series data handling, regression modeling, and performance evaluation in financial forecasting.

---

## Dataset

The dataset consists of approximately **15 years of historical PSEi records**, covering October 2011 to October 2026.

The original dataset contains 3,659 observations with historical market information, including date, OHLC prices, and trading volume. Additional technical indicators were calculated manually using Microsoft Excel.

After accounting for the moving averages and future target values, the final dataset used in the model contains **3,603 observations**.

### Features

#### Historical Market Data
- Price (Closing Price)
- Open
- High
- Low
- Volume

#### Technical Indicators

- **50-day Simple Moving Average (SMA):** Measures the underlying price trend by calculating the average closing price over the previous 50 trading days.
- **14-day Relative Strength Index (RSI):** Measures market momentum by comparing average gains and losses over a 14-day period using Wilder's smoothing method.
- **14-day Average True Range (ATR):** Measures market volatility by accounting for daily price movements and gaps between consecutive trading sessions.

#### Target Variable
- **Next Week Price:** The PSEi closing price approximately five trading days ahead.

**Dataset Source**

- [Investing.com – PSEi Composite Historical Data](https://ph.investing.com/indices/psei-composite-historical-data)

**Note:** The original dataset was already cleaned and contained no missing values. Technical indicators and other derived variables were computed separately in Excel before being imported into Python.

---

## Methodology

The project follows a supervised machine learning regression workflow:

1. **Data Preparation**
   - Importing historical PSEi data.
   - Selecting relevant features.
   - Converting date values into appropriate data types.
   - Checking data types and missing values.

2. **Feature Engineering**
   - Computing the 50-day Simple Moving Average.
   - Computing the 14-day Relative Strength Index using Wilder's smoothing.
   - Computing the 14-day Average True Range using Wilder's smoothing.
   - Preparing the five-trading-day-ahead target variable.

3. **Exploratory Data Analysis (EDA)**
   - Pairplot visualization.
   - Feature correlation analysis using heatmaps.
   - Historical closing price and SMA visualization.
   - Trading volume analysis.
   - Volatility and momentum visualization.

4. **Data Splitting**
   - Chronological train-test splitting.
   - Using the newest 20% of observations as the test set.
   - Training on older observations while excluding a five-row gap between training and testing data to account for the forecasting horizon.

5. **Model Development**
   - Linear Regression
   - Random Forest Regressor
   - XGBoost Regressor

6. **Model Evaluation**
   - Mean Absolute Error (MAE)
   - Mean Squared Error (MSE)
   - Root Mean Squared Error (RMSE)
   - Coefficient of Determination (R²)
   - Comparison against the Naive Walk baseline.

7. **Forecast Visualization**
   - Comparing predicted and actual PSEi prices.
   - Visualizing model predictions against the Naive Walk baseline.

---

## Results

The models were evaluated using the same chronological test set and compared against the Naive Walk baseline, which uses the current closing price as the forecast for the next week.

| Model | MAE | MSE | RMSE | R² |
|:-------------------------------|:-----------:|:-----------:|:-----------:|:-----------:|
| **Linear Regression** | 103.0730 | **17,476.3246** | **132.1981** | **0.8779** |
| Naive Walk (5-days) | **102.9481** | 17,649.6202 | 132.8519 | 0.8767 |
| XGBoost | 106.3507 | 18,436.4067 | 135.7807 | 0.8712 |
| Random Forest | 106.7995 | 18,626.0367 | 136.4772 | 0.8699 |

### Interpretation

- **Linear Regression** demonstrated the strongest overall performance, achieving the lowest MSE and RMSE and the highest R² among the evaluated models. However, its MAE was marginally higher than the Naive Walk baseline.
- **Naive Walk** remained a highly competitive benchmark, achieving a slightly lower MAE than Linear Regression. This highlights the difficulty of improving upon simple random-walk forecasts in financial time series.
- **XGBoost and Random Forest** did not outperform the Naive Walk across the evaluated metrics, suggesting that increased model complexity did not necessarily translate into better forecasting performance.
- The relatively small performance differences between Linear Regression and the Naive Walk suggest that much of the predictive information may already be captured by the current PSEi price.

Overall, the results demonstrate that simpler regression approaches can remain competitive alternatives to more complex machine learning algorithms in financial forecasting.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Microsoft Excel
- Google Colab

---

## Repository Structure

```text
├── PSEi_Predictor_Model.ipynb
├── psei_data (1).csv
├── README.md
```

---

## Future Improvements

Potential extensions include:

- Exploring additional technical indicators and macroeconomic variables such as exchange rates, inflation, and interest rates.
- Investigating alternative forecasting approaches, including ARIMA, SARIMAX, and other statistical time-series models.
- Experimenting with time-series-specific machine learning techniques and expanding the model comparison.
- Applying rolling-window or walk-forward validation to evaluate model stability across different market conditions.
- Exploring return-based forecasting and directional classification instead of predicting absolute index prices.
- Investigating whether additional features can meaningfully outperform the Naive Walk baseline.
- Incorporating external market information and economic events to account for factors beyond historical data and technical indicators.

---

## Disclaimer

This project is intended for educational and research purposes only. The forecasts generated by the models should not be interpreted as financial advice or definitive indicators of future market performance. Stock market movements are inherently uncertain and are influenced by numerous external factors that may not be captured by historical data and technical indicators alone.

---

## Author

**Jerick L. Garcia**

Bachelor of Science in Mathematics  
**University of the Philippines Diliman**
